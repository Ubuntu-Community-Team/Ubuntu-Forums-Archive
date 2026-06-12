---
title: "Gnome Panel problems"
date: 2008-12-22
forum: General Help
---

### Post by ryanferreri on 2008-12-22
Hello there,

I am having various problems with my top panel. First of all, I cannot add icons to it anymore. If I right-click an item in the Applications menu and click 'Add to Panel,' it does not add the icon. If I right-click the panel and click 'Add to Panel...' and select something from the list, that item does not appear.

Another problem involves Firefox and the panel. I'm not sure if this is related or not. Sometimes when I open Firefox, it takes up the whole screen. The panels (top and bottom) are covered up, and the standard menus are there (File, Edit, View, etc.) but the Minimize, Maximize and close buttons are not there. I have to use Alt-Tab to switch applications. The behavior comes back after a reboot.

Please let me know if there is any more information needed. I'm running Ubuntu 8.10 x64. Gnome-Panel is version 1:2.24.1-0ubuntu2.1 according to Synaptic

Thanks!

---

### Post by drs305 on 2008-12-22
> **ryanferreri said:**
> Another problem involves Firefox and the panel. I'm not sure if this is related or not. Sometimes when I open Firefox, it takes up the whole screen. The panels (top and bottom) are covered up, and the standard menus are there (File, Edit, View, etc.) but the Minimize, Maximize and close buttons are not there. I have to use Alt-Tab to switch applications. The behavior comes back after a reboot.


This or something similar has been reported as a bug. There are a couple of solutions that have been successful for some users.

From easiest to most extreme:

1. Hit F11 twice. This will maximize it and then restore it to the original size. Once you have done that resize it at least slightly smaller than full screen and close it. 

If you use compiz (and want to keep it):
2a. System, Preferences, CompizConfiguration Settings Manager (if not installed, sudo apt-get install compizconfig-settings-manager). General tab and untick "Undirect Full Screen Windows".

2b. Once again in compiz, Utility, tick the Workarounds box and untick "Legacy Fullscreen Support". Alternatively, if you have Workarounds ticked, untick it.

3. Stop all special effects: System, Preferences, Appearance, Visual Effects, None.

---

### Post by LoneWolfJack on 2008-12-22
you did unlock the panel, right? ;)

other than that... did you try creating an entire new panel with the icons you need? this would help validate whether just that specific panel config got stuck or if it is a general problem.

---

### Post by ryanferreri on 2008-12-23
Yeah I am unable to create a new panel. If I right-click on an existing panel and select New-Panel, it does nothing.

---

### Post by ryanferreri on 2008-12-26
Here's an interesting twist - I use NoMachine NX for remote access to this machine. On the remote sessions, I am able to use the full functionality of the Panel. In fact, icons that I have placed on the panel, which do not show up when I'm at the console, do show up in remote sessions.

---

### Post by northern lights on 2008-12-26
Have you tried reinstalling it?

Either by running,```
sudo apt-get --reinstall install gnome-panel
```
or, which is what I'd prefer, ```
sudo aptitude purge gnome-panel
``````
sudo apt-get update && sudo apt-get install gnome-panel
```

---

