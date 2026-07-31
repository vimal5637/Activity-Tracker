# 🏃 9-to-5 Weight Loss Tracker

A beautiful, single-page Progressive Web App (PWA) designed to track a structured 30-day (22-weekday) weight loss routine. Built with a modern, mobile-first fitness theme, it features local storage persistence, real-time analytics, hourly desktop/mobile notifications, and Google Fit integration.

---

## 🌟 Key Features

### 1. 📅 30-Day Weekday Tracking Grid
*   **22-Weekday Columns**: Focuses purely on weekdays (Monday to Friday) across a standard 30-day month, excluding weekends.
*   **Sticky Labels & Horizontal Scroll**: The task labels column is frozen on the left while the 22 day columns scroll smoothly horizontally, making it extremely easy to read on mobile and laptop screens.
*   **Custom Checkboxes**: Large, touch-friendly checkboxes with emerald green active states.

### 2. 📊 Real-Time Analytics Engine
*   **Daily Completion %**: Dynamically calculates the percentage of completed tasks for each day at the bottom of the grid.
*   **Weekly Block Progress**: Below the grid, progress is grouped and visualized in 5-day blocks:
    *   **Week 1**: Days 1–5
    *   **Week 2**: Days 6–10
    *   **Week 3**: Days 11–15
    *   **Week 4**: Days 16–20
    *   **Week 5**: Days 21–22
*   **Overall Monthly Success Dashboard**: A prominent circular progress ring at the top of the dashboard showing your overall average across all 22 weekdays.
*   **Perfect Days Streak**: Tracks your longest consecutive streak of 100% completed days.

### 3. ⏰ Hourly Reminders (Web Notifications)
*   **Hourly Desk Walks**: Triggers a notification every hour on the hour between 9:00 AM and 5:00 PM to stand up and walk for 5 minutes.
*   **Green Tea Reminders**: Triggers notifications at 10:30 AM (Cup 1) and 3:30 PM (Cup 2).
*   **Active Keep-Alive**: Works seamlessly as long as the tab is open or running in a background browser window.

### 4. 🔗 Google Fit Integration
*   **OAuth 2.0 Integration**: Securely log in with your Google account directly from the browser.
*   **Auto-Check Targets**: Once connected, the app fetches your daily distance. If you meet the thresholds, it **automatically checks off** your **🏃 4km Jog** and **🚶 3km Walk** tasks for the day!
*   **Simulate/Mock Sync**: Don't have a Google Client ID yet? No problem! Use the **Mock Sync** button in the Google Fit panel to instantly simulate a successful sync and see how the auto-checking works.

### 5. 💾 Data Portability & Safety
*   **Local Storage Persistence**: All your progress, settings, and connections are saved automatically in your browser's local storage.
*   **Backup & Restore**: Export all your data as a JSON file to back up your progress, or import a backup file to restore it.
*   **Reset Option**: Clear all progress to start a fresh 30-day challenge.

---

## 🛠️ The 12 Daily Routine Tasks

1.  🌅 **Hydrate (2 Glasses Water)** - *All Day*
2.  🏃 **4km Jog (30 Mins)** - *Morning* (Auto-checks via Google Fit)
3.  🍳 **Protein & Fruit Breakfast** - *Morning*
4.  🚶 **Hourly 5-Min Desk Walks** - *9 AM - 5 PM* (Hourly notification reminder)
5.  🍵 **Green Tea Cup 1 (10:30 AM)** - *10:30 AM* (Notification reminder)
6.  🥗 **Balanced Nutrient Lunch** - *Afternoon*
7.  🍵 **Green Tea Cup 2 (3:30 PM)** - *3:30 PM* (Notification reminder)
8.  🥜 **Pre-Walk Mini Snack** - *Afternoon*
9.  🚶 **3km Walk (30 Mins)** - *Evening* (Auto-checks via Google Fit)
10. 🍽️ **Shifted Dinner (8:00 PM)** - *8:00 PM*
11. 💤 **Digital Detox & Sleep (10 PM)** - *10:00 PM*
12. ❌ **Zero Sugar Maintained** - *All Day*

---

## 🚀 How to Run the App

### Option 1: Run Locally (Quick Start)
You can run this app directly from your computer:
1. Double-click the `index.html` file to open it in Google Chrome.
2. *Note: When running via the `file://` protocol, browser security policies will restrict Google Fit OAuth and PWA installation. To use these features, use Option 2 or 3.*

### Option 2: Run a Simple Local Server
To enable Service Workers (PWA) and Google Fit locally, run a simple HTTP server in the project folder:
```bash
# Using Python 3
python -m http.server 8000

# Using Node.js (npx)
npx serve .
```
Then open `http://localhost:8000` in Google Chrome.

### Option 3: Host for Free (Recommended for Mobile)
To install the app on your phone and use Google Fit on the go, host the files on a secure `https://` domain for free:
*   **GitHub Pages**: Push this directory to a GitHub repository, go to Settings > Pages, and enable GitHub Pages.
*   **Vercel / Netlify**: Drag and drop the folder into Vercel or Netlify for instant deployment.

---

## 📱 How to Install on Mobile (PWA)

Once your app is hosted on an `https://` domain (like GitHub Pages or Vercel):

### On iOS (Safari)
1. Open the hosted URL in **Safari**.
2. Tap the **Share** button (box with an up arrow).
3. Scroll down and tap **Add to Home Screen**.
4. Tap **Add** in the top right. The app will now appear on your home screen with its own icon and open in full-screen mode!

### On Android (Chrome)
1. Open the hosted URL in **Google Chrome**.
2. Tap the **three dots** menu icon in the top right.
3. Tap **Install app** or **Add to Home Screen**.
4. Follow the prompts to install.

---

## 🔑 Setting up Google Fit OAuth Client ID

To use real Google Fit syncing:
1. Go to the [Google Cloud Console](https://console.cloud.google.com/).
2. Create a new project.
3. Search for **Fitness API** and enable it.
4. Go to **APIs & Services > Credentials**.
5. Click **Configure Consent Screen** (select External, fill in basic app details, and add the scope `.../auth/fitness.activity.read`).
6. Go back to **Credentials**, click **Create Credentials > OAuth Client ID**.
7. Select **Web Application** as the Application Type.
8. Under **Authorized JavaScript origins**, add your hosted domain (e.g., `https://yourusername.github.io` or `http://localhost:8000`).
9. Under **Authorized redirect URIs**, add the exact URL of your app (e.g., `https://yourusername.github.io/weight-loss-tracker/` or `http://localhost:8000/index.html`).
10. Copy the generated **Client ID**, paste it into the Google Fit Connection panel in the app settings, and tap **Authenticate & Connect**!
