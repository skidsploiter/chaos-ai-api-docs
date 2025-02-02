## 📜Chaos AI API Documentation
---
# AI Query API Documentation

## Base URL
```
http://172.96.161.161:6969/api/ai
```

## Endpoint
### `GET /api/ai`
Retrieves AI-generated responses based on the provided query.

### Parameters
| Parameter | Type   | Description                        |
|-----------|--------|----------------------------------|
| `query`  | string | The input text for the AI to process. |
| `uid`    | string | A unique identifier for the user. |

### Example Request
```bash
curl "http://172.96.161.161:6969/api/ai?query=hello&uid=6969"
```

### Example Response
```json
{
    "response": "Hello! How can I help you?"
}
```

---

## 🐍 Python Tutorial

```python
import requests

API_URL = "http://172.96.161.161:6969/api/ai"

def query_ai(text, uid="6969"):
    params = {
        "query": text,
        "uid": uid
    }
    response = requests.get(API_URL, params=params)
    if response.status_code == 200:
        return response.json()
    else:
        return {"error": f"Failed with status {response.status_code}"}

# Example Usage
result = query_ai("Hello, AI!")
print(result)
```

---

## 💻 C# Tutorial

```csharp
using System;
using System.Net.Http;
using System.Threading.Tasks;

class Program
{
    private static readonly HttpClient client = new HttpClient();

    public static async Task QueryAI(string query, string uid = "6969")
    {
        string url = $"http://172.96.161.161:6969/api/ai?query={Uri.EscapeDataString(query)}&uid={uid}";
        HttpResponseMessage response = await client.GetAsync(url);
        
        if (response.IsSuccessStatusCode)
        {
            string responseBody = await response.Content.ReadAsStringAsync();
            Console.WriteLine(responseBody);
        }
        else
        {
            Console.WriteLine($"Error: {response.StatusCode}");
        }
    }

    static async Task Main(string[] args)
    {
        await QueryAI("Hello, AI!");
    }
}
```
