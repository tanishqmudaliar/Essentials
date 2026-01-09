# PythonAnywhere Auto-Renewal

Automatically renew your PythonAnywhere free web app every 15 days using GitHub Actions.

## 🚀 Features

- Automated renewal every 15 days (before the 1-month expiry)
- GitHub Actions workflow with keepalive (prevents workflow from being disabled)
- Secure credential management using GitHub Secrets
- Manual trigger option for testing

## 📋 Setup Instructions

### 1. Fork or Clone This Repository

```bash
git clone https://github.com/YOUR_USERNAME/pythonanywhere-auto-renew.git
cd pythonanywhere-auto-renew
```

### 2. Add GitHub Secrets

1. Go to your repository on GitHub
2. Click **Settings** → **Secrets and variables** → **Actions**
3. Click **New repository secret**
4. Add these two secrets:
   - **Name:** `PA_USERNAME` | **Value:** Your PythonAnywhere username
   - **Name:** `PA_PASSWORD` | **Value:** Your PythonAnywhere password

### 3. Enable Workflow Permissions

1. Go to **Settings** → **Actions** → **General**
2. Scroll to **Workflow permissions**
3. Select **Read and write permissions**
4. Click **Save**

### 4. Test the Workflow

1. Go to **Actions** tab in your repository
2. Click on **Auto-Renew PythonAnywhere** workflow
3. Click **Run workflow** → **Run workflow**
4. Wait for it to complete and check the logs

## 🧪 Local Testing

### Prerequisites

- Python 3.9+
- PythonAnywhere account

### Steps

1. Install dependencies:
```bash
pip install -r requirements.txt
```

2. Create a `.env` file:
```env
PA_USERNAME=your_username
PA_PASSWORD=your_password
```

3. Run the script:
```bash
python renew_app.py
```

## 📅 Schedule

The workflow runs automatically:
- **Every 1st of the month** at 04:00 UTC
- **Every 15th of the month** at 04:00 UTC

You can also trigger it manually anytime from the Actions tab.

## 🔒 Security

- Credentials are stored as encrypted GitHub Secrets
- Never commit your `.env` file (it's in `.gitignore`)
- The script uses HTTPS for all API calls

## ⚠️ Important Notes

- **GitHub disables workflows** after 60 days of repository inactivity. The keepalive action prevents this by making automatic commits.
- **PythonAnywhere free tier** expires after 1 month of inactivity (updated Jan 2026).
- This script uses web scraping, so it may break if PythonAnywhere changes their website structure.

## 🐛 Troubleshooting

### Workflow fails with "Login failed"
- Verify your `PA_USERNAME` and `PA_PASSWORD` secrets are correct
- Check if PythonAnywhere has changed their login page

### "No extend button found"
- This is normal if your app doesn't need renewal yet
- The script will try again on the next scheduled run

### Workflow is disabled
- Make sure you have "Read and write permissions" enabled
- The keepalive action should prevent this automatically

## 📝 License

MIT License - feel free to use and modify!

## 🤝 Contributing

Issues and pull requests are welcome!

---

**Made with ❤️ for PythonAnywhere users**
