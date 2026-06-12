---
title: "windowmaker dock for xfce panel"
date: 2012-01-09
forum: Desktop Environments
---

### Post by GraeW on 2012-01-09
I just reinstalled Ubuntu on my laptop, and went through the usual tweaks to make everything look "just right" as I like it. Although I used to use WindowMaker a lot in the past, I have also used XFCE and usually bounce between the two.
 
My problem is with the windowmaker dock "applet" for the XFCE panel - I had it working at first, and then my computer locked up on me (it is an older laptop which tends to get hot, and rarely this locks the screen up). When I rebooted, I saw all of my WM dock apps on top of each other in the upper left corner, and the panel app showing the "dead mouse" X and none of the apps loaded there as they should. Closing the apps and trying to restart them only brings them back to the desktop, not the XFCE panel. Likewise, killing the panel app and restarting "from scratch" still won't get the dock apps to be swallowed as they should be.
 
I'm no great guru with linux but I'm not afraid of CLI or manipulating a config file. Just need to know where to look and what to fix or delete.
 
Thanks!
 
p.s. - I did look through the XFCE forums on the related website/wiki, but it was rather vague on files and editing, and there was no supporting information on the WM Dock other than "plug it in and it works"..

---

### Post by GraeW on 2012-01-10
gratuitous bumpage for a new day ;)

---

### Post by Frogs Hair on 2012-01-10
I don't know if Xubuntu has an equivalent to hidden folders in the file browser as ubuntu does .

When I used a dock prior to Unity there was a hidden folder with the configuration . If the folder became corrupt or I changed the configuration in a way I didn't like , I would shut down the dock , delete folder and reinstall the dock . 

If you just try and reinstall the dock and the configuration is not removed the same problem will occur with the new installation .

---

### Post by GraeW on 2012-01-10
Yeah, I've tried to do that, including completely removing xubuntu/xfce and reinstalling each one. I have tried to look through the hidden files and .directory listings, but nothing pops out at me directly related to that WMDock thing even in the config files I've seen for the XFCE panel.
 
I will keep looking, though.. thanks!

---

### Post by Toz on 2012-01-10
You might also want to check to see if the xfce panel application is running?
```
ps -ef | grep xfce4-panel | grep -v grep
```
It would need to be for the applet to work properly. Sometimes when you crash out or prematurely exit from xfce, some of the required applications don't startup automatically on the next login.

---

### Post by GraeW on 2012-01-10
the panel IS running. I have plenty of other gadgets, app menu, pager, and notification area there. it is just this one panel widget that won't swallow the WM apps anymore.

---

### Post by GraeW on 2012-01-11
I had some time to tweak today during my lunch break. Not sure how I did it, but the dock is now working again. The only thing I did was select then de-select the bottom option of the WM Dock options (allowing any WindowMaker app to be swallowed) and things started working properly. I had it de-selected before, but after selecting it, restarting (logoff/on) and then de-selecting again it worked.
 
Don't ask me why I tried to do that.. I still don't see where the info is stored (config or rc file) but at least I have the information looking the way I want again.

---

