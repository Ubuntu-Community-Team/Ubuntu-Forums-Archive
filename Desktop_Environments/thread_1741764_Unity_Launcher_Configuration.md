---
title: "Unity Launcher Configuration"
date: 2011-04-28
forum: Desktop Environments
---

### Post by biomedtek on 2011-04-28
How do you access preferences for changing size of the launcher bar or icon size, etc? I looked through system settings and could not find it.

---

### Post by Copper Bezel on 2011-04-28
Make sure you have the CompizConfig Settings Manager, which manages the settings for the plugins of the window manager including the Unity UI, installed:

```
sudo apt-get install compizconfig-settings-manager
```

Then run it from Preferences and find the Unity plugin. All the settings are in there.

---

### Post by erasmusp on 2011-04-28
Firstly Make sure you have the CompizConfig Settings Manager installed.

Launch CCSM(Super + a and search for CCSM) and then browse to Ubuntu Unity Plugin. Choose 'Experimental' tab.

Adjust the value of 'Launcher Icon Size' by simple scrolling. The default value of 'Launcher Icon Size' is 48, but I like it around 40...

---

### Post by biomedtek on 2011-04-28
Thanks, I installed CCSM.
I didn't see an option to auto-hide the launcher, is this not available.
I would like to hide the bar until I move the cursor to the edge of the screen.

---

### Post by TurtleKing on 2011-05-08
Came upon this thread by google-fu. If you still have not found it, the appear on mouse over should be set by default, but there is also an option to set it how you want it in the behavior tab "Hide launcher".

---

