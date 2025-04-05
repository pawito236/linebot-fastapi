# LINE Translation Bot

This project is a LINE Messaging API bot that translates messages from Thai to English using Google's Gemini AI model. The bot receives messages through LINE, processes them with Google's generative AI, and replies with the translated text.

## Features

- Translates messages from Thai to English
- Built with FastAPI for efficient API handling
- Uses the LINE Messaging API for communication
- Leverages Google's Gemini 2.0 Flash model for high-quality translations

## Prerequisites

- Python 3.10
- A LINE developer account with a created Messaging API channel
- A Google API key with access to Gemini models

## Installation

1. Clone this repository:
   ```bash
   git clone <repository-url>
   cd line-translation-bot
   ```

2. Install dependencies:
   ```bash
   pip install fastapi uvicorn python-dotenv linebot langchain-google-genai
   ```

3. Create a `.env` file in the project root directory:
   ```
   LINE_CHANNEL_SECRET=your_line_channel_secret
   LINE_CHANNEL_ACCESS_TOKEN=your_line_channel_access_token
   GOOGLE_API_KEY=your_google_api_key
   ```

## Configuration

### LINE Messaging API Setup

1. Create a LINE developer account at [developers.line.biz](https://developers.line.biz/)
2. Create a new provider and channel for the Messaging API
3. Obtain your Channel Secret and Channel Access Token from the Basic Settings page
4. Add these credentials to your `.env` file

### Google Gemini API Setup

1. Create or use an existing Google Cloud project
2. Enable the Gemini API for your project
3. Create an API key in the Google Cloud Console
4. Add the API key to your `.env` file as `GOOGLE_API_KEY`

## Running the Bot

1. Start the FastAPI server:
   ```bash
   uvicorn main:app --reload
   ```

2. Expose your local server using a tool like ngrok:
   ```bash
   ngrok http 8000
   ```

3. Set the Webhook URL in your LINE channel's Messaging API settings to:
   ```
   https://your-ngrok-url/callback
   ```

## Usage

1. Add your LINE bot as a friend using the QR code or LINE ID from your LINE developer console
2. Send a message in Thai to your bot
3. The bot will reply with the English translation of your message

## Customization

- To change the translation direction or languages, modify the parameters in the `translate` function call in the `handle_callback` function
- Adjust the model parameters in the `llm` initialization for different translation behavior

## Troubleshooting

- If you see "Invalid signature" errors, check that your LINE_CHANNEL_SECRET is correct
- If translations aren't working, verify your GOOGLE_API_KEY is valid and has the necessary permissions
- For webhook issues, ensure your server is publicly accessible and the webhook URL is correctly set in the LINE developer console
