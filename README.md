# Groq API with Python

This project demonstrates how to interact with Groq-hosted LLMs using Python.

## Features

* Load API keys securely using `.env`
* Send requests using the `requests` library
* Use the OpenAI SDK with Groq
* Generate responses from the Llama 3.3 70B model

## Requirements

```text
python-dotenv
requests
openai
```

## Setup

1. Create and activate a virtual environment.
2. Install dependencies:

```bash
pip install -r requirements.txt
```

3. Create a `.env` file:

```env
GROQ_API_KEY=your_api_key_here
```

## Usage

Load the API key:

```python
from dotenv import load_dotenv
import os

load_dotenv()
GROQ_API_KEY = os.getenv("GROQ_API_KEY")
```

Create a Groq client:

```python
from openai import OpenAI

client = OpenAI(
    api_key=GROQ_API_KEY,
    base_url="https://api.groq.com/openai/v1"
)
```

Generate a response:

```python
response = client.chat.completions.create(
    model="llama-3.3-70b-versatile",
    messages=[
        {"role": "user", "content": "What is Bayes' theorem?"}
    ]
)

print(response.choices[0].message.content)
```

## Notes

* Keep your API key private.
* Do not commit the `.env` file to GitHub.
* Ensure the correct virtual environment/kernel is selected when using Jupyter notebooks.
