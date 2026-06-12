---
title: "Top menu bar and bottom navigation bar don't load"
date: 2010-11-29
forum: Desktop Environments
---

### Post by Skynyrd9 on 2010-11-29
So out of the blue this morning when i started ubuntu and logged in the top bar and bottom navigation bars wouldn't load. I did recently uninstall some software, but i had successfully restarted and logged in multiple times since. So im not really sure what is going on.  Also im currently running 64 bit 10.10.

---

### Post by nalgarryn on 2010-11-30
Hopefully you have a hotkey for starting a terminal window.

I think it defaults to Ctrl+Alt+T. I changed mine to Mod4+T (Windows+T)

Open a terminal or go Crtl+Alt+F1 and type 

```
killall gnome-panel
``` this should kill the process and it automagically restarts. This is useful if your panel applets don't load, or the top but not the bottom does.

If for whatever reason it does not automagically restart, you can type 

```
gnome-panel &
```

---

### Post by Skynyrd9 on 2010-11-30
That worked to a point. Apparently gnome-panel got uninstalled.  Also how to i make it so the pannels will stay alive after i close the terminal, because currently when i close the terminal i loss the pannels.

---

### Post by nalgarryn on 2010-11-30
I'm not expert enough to help you, probably.

& attaches a process to the current environment.

If you want to install, you can try 

```
sudo apt-get install gnome-panel 
```

If it says that you already have the latest version then it is installed properly.

---

