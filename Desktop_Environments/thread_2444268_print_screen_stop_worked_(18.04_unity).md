---
title: "print screen stop worked (18.04 unity)"
date: 2020-05-27
forum: Desktop Environments
---

### Post by jarekgol on 2020-05-27
So few days (or weeks) ago Print Screen key stop working. It doesn't launch `gnome-screenshot` which it used to do, nor place screenshots in ~/Pictures nor ~/Obrazy (polish word for pictures). Launching `gnome-screenshot` from terminal works fine. I also go to Settings/Keyboard/Shortcuts/Screenshots  disable "Make screenshot" with backspace (said to me OFF) and add my shortcut to `gnome-screenshot` and press print screen as key that appear as Print - which prove that key is working and info about key press get to system. Also xev show something when I press it.
I checked dmesg and syslog, but nothing there right after pressing key.
I do not know where to search next, but I'm 100% sure that it works before.

---

