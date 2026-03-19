[README.md](https://github.com/user-attachments/files/26108324/README.md)
# Command Term Analyser — Deployment Guide

## What's in this folder

```
command-term-analyser/
├── index.html                        ← The web page
├── netlify.toml                      ← Netlify configuration
├── netlify/
│   └── functions/
│       └── analyse.js                ← Secure API proxy (holds your API key)
└── README.md                         ← This file
```

---

## Step 1 — Get your Anthropic API key

1. Go to https://console.anthropic.com and sign in (or create a free account)
2. Click **API Keys** in the left sidebar
3. Click **Create Key**, give it a name (e.g. "command-term-analyser"), copy the key
4. Keep this key private — never share it or put it in your HTML file

---

## Step 2 — Create a GitHub account and upload the files

1. Go to https://github.com and create a free account
2. Click the **+** icon (top right) → **New repository**
3. Name it `command-term-analyser`, set it to **Public**, click **Create repository**
4. On the next screen, click **uploading an existing file**
5. You need to upload the files maintaining this folder structure:
   - `index.html`
   - `netlify.toml`
   - `netlify/functions/analyse.js`
6. For the subfolder: click **Create new file**, type `netlify/functions/analyse.js` as the filename — GitHub will create the folders automatically. Paste the contents of `analyse.js`.
7. Repeat for `index.html` and `netlify.toml`
8. Click **Commit changes** after each file

---

## Step 3 — Deploy on Netlify

1. Go to https://netlify.com and create a free account (you can sign in with GitHub)
2. Click **Add new site** → **Import an existing project**
3. Choose **GitHub** and authorise Netlify to access your account
4. Select your `command-term-analyser` repository
5. Leave all build settings as default (no build command needed)
6. Click **Deploy site**
7. Netlify will give you a live URL like `https://random-name.netlify.app`

---

## Step 4 — Add your API key (critical)

The site will be live but won't work yet — you need to add your API key as a secret environment variable:

1. In Netlify, go to your site → **Site configuration** → **Environment variables**
2. Click **Add a variable**
3. Key: `ANTHROPIC_API_KEY`
4. Value: paste your API key from Step 1
5. Click **Save**
6. Go to **Deploys** and click **Trigger deploy** → **Deploy site** to restart with the new key

Your site is now live and fully working! 🎉

---

## Step 5 (optional) — Set a custom name

To change your URL from `random-name.netlify.app` to something like `hms-analyser.netlify.app`:

1. In Netlify → **Site configuration** → **Site details** → **Change site name**
2. Type your preferred name and save

To use your own domain (e.g. `www.yoursite.com.au`):
1. Buy a domain from Crazy Domains, GoDaddy, or Namecheap (~$15–20/year)
2. In Netlify → **Domain management** → **Add a domain**
3. Follow the instructions to point your domain at Netlify

---

## Updating the site later

To make changes to the tool:
1. Edit `index.html` directly on GitHub (click the file → pencil icon)
2. Commit the change
3. Netlify automatically re-deploys within ~30 seconds

---

## Cost

- **Netlify free tier**: 100GB bandwidth/month, 125,000 function calls/month — more than enough for a classroom tool
- **Anthropic API**: Pay per use. Claude Sonnet is approximately $0.003 per analysis (very cheap). You can set a spending limit in the Anthropic console.
