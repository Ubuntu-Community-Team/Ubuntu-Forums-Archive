---
title: "Help, can't create icons or new folders on desktop..."
date: 2008-11-30
forum: Desktop Environments
---

### Post by Jynxxander on 2008-11-30
I followed these steps to get different wallpapers for each desktop

I. Disable "show desktop" in Nautilus
1. ALT+F2
2. gconf-editor
3. Apps --> Nautilus --> Preferences
4. Untick "show desktop"

II. Install Compiz Fusion
1. In Terminal, input the following:
Code:

sudo aptitude install compizconfig-settings-manager

2. Exit Terminal

III. Select your desktop wallpaper
1. System --> Preferences --> Advanced Desktop Settings
2. Tick "Desktop Cube" and opt to disable desktop wall if prompted
3. Tick "Rotate Cube"
4. Select "Desktop Cube"
5. Click "Appearance" tab
6. Click "Add" under the "Background Images" field
7. Browse for your desired wallpaper(s), ordering them based on which face of the cube you want them to appear


But after editing Nautilus preferences, all my icons are gone from my desktop, I can't create a new folder on my desktop (Can't access contextual menu.

Does anyone know how to fix this?

---

### Post by gettinoriginal on 2008-12-01
I found that when I applied this, it in essence "covered" my desktop with the wallpaper.  I had to go to > places > desktop to view my desktop.  I finally went back to just using a single desktop wallpaper.

---

