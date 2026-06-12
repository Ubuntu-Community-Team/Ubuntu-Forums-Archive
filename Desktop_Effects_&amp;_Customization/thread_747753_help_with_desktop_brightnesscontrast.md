---
title: "help with desktop brightness/contrast"
date: 2008-04-06
forum: Desktop Effects &amp; Customization
---

### Post by flugo on 2008-04-06
I was messing around with customizing my desktop and now my wallpaper screen is very dark, can hardly see the icons. I have no idea how i managed to do this and am lost in trying to find a solution. any programs i open, including firefox are fine , my desktop is the only thing that seems to be affected. any suggestions are appreciated.

EDIT:
I traced back my problem to a thread that described how to have a different wallpaper for each desktop for the cube. i unticked desktop cube and everything brightened back up. I probably missed something in the instructions. Will go back and redo. This is what i was following:

To have different wallpapers for each desktop, follow these steps:

**I. Disable "show desktop" in Nautilus**
1. ALT+F2
2. gconf-editor
3. Apps --> Nautilus --> Preferences
4. Untick "show desktop"

**II. Install Compiz Fusion**
1. In Terminal, input the following:
```
sudo aptitude install compizconfig-settings-manager
```
2. Exit Terminal

**III. Select your desktop wallpaper**
1. System --> Preferences --> Advanced Desktop Settings
2. Tick "Desktop Cube" and opt to disable desktop wall if prompted
3. Tick "Rotate Cube"
4. Select "Desktop Cube"
5. Click "Appearance" tab
6. Click "Add" under the "Background Images" field
7. Browse for your desired wallpaper(s), ordering them based on which face of the cube you want them to appear[/QUOTE]

I'm not sure if i screwed something up but just in case someone else tries this and your desktop turns out very dark untick desktop cube in compizconfig settings manager and it will go back to normal.

---

