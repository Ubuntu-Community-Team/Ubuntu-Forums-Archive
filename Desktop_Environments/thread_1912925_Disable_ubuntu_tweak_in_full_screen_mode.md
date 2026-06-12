---
title: "Disable ubuntu tweak in full screen mode"
date: 2012-01-21
forum: Desktop Environments
---

### Post by najdorfchess on 2012-01-21
Hi all. I'm using Ubuntu 10.10 64-bit with Macbuntu theme (along with Ubuntu-tweak and Compiz) and Cairo dock UI (yes you guessed it, I'm not a fan of Unity interface at all ;)
I have enabled workspace edge in ubuntu tweak so that when I roll my mouse to the left corner of the screen it removes all the open windows and show my desktop and the right corner for showing all the current open windows (just like mission control in Mac OS X). Anyway I have the issue that it sometimes becomes annoying in full screen application (say I'm running another OS in Virtual Machine), when I accidentally move my mouse to that corner it does the desktop edge action which is kinda annoying. Is there a way to disable that when I'm on full screen mode? Thanks

---

### Post by stinkeye on 2012-01-21
What you could do is use the commands plugin in compiz to set a screen edge plus left mouse to show the desktop.

You will need to install xdotool.
```
sudo apt-get install xdotool
```

Disable the ubuntu tweak screen edge setting.
Open ccsm > general options > Commands.

Add this line to one of the command boxes as in first pic.
(Check in ccsm > general options > key bindings
to see the keyboard shortcut for **Show Desktop**.)
```
xdotool key ctrl+alt+d
```


Then in the corresponding command number in the **Button Bindings** Tab 
set a screen edge/corner and mouse button 1.

---

### Post by najdorfchess on 2012-01-21
Thanks for your reply. What does that do? I didn't get it. I did install xdotool but I couldn't find the section you are referring to in ccsm.

---

### Post by stinkeye on 2012-01-22
Xdotool allows you to execute key strokes in the commandline.
So by using the ccsm commands plugin you can set show desktop  to a screen-edge + mouse button instead of just a screen-edge.
Check that **ctrl+alt+d** is set to show your desktop.

ccsm is **compizconfig-settings-manager**.
```
sudo apt-get install compizconfig-settings-manager
```

to run ... press alt+F2 and enter ccsm.

---

### Post by najdorfchess on 2012-01-22
Yes I do have ccsm installed, ctrl + alt + d isn't showing the desktop. I guess the macbuntu theme might have changed the setting. I still didn't understand where you want me to add it in in ccsm.

---

### Post by stinkeye on 2012-01-22
> check in ccsm > general options > key bindings
 to see the keyboard shortcut for show desktop.
Set it to **ctrl+alt+d** if needed.
[attach]211280[/attach][attach]211281[/attach]



> **najdorfchess said:**
> i still didn't understand where you want me to add it in in ccsm.
[attach]211282[/attach][attach]211283[/attach][attach]211284[/attach]

---

