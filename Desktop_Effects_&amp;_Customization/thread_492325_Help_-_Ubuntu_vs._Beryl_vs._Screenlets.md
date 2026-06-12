---
title: "Help - Ubuntu vs. Beryl vs. Screenlets?"
date: 2007-07-04
forum: Desktop Effects &amp; Customization
---

### Post by nehuenmingote on 2007-07-04
[SIZE="3"]Hi everyone! 
I'm in a desperate seek for help.
I've been using Ubuntu and Beryl for about two months, Avant WIndow Manager for a month, and Screenlets for some weeks with no trouble at all. Some hours ago, when I started up my PC, I discovered this, and I don't know how to solve it:


[IMG]http://www.freewebtown.com/nehuenmingote/desktop.jpg[/IMG]


Beryl is running, but it doesn't seem to be working. I tried restarting my pc, beryl, screenlets, avant-window manager, but nothing happened. I thought of the NVidia drivers, I reinstalled them, without success.
Can someone please help me?

My PC:

Intel(R) Pentium(R) 4 CPU 2,40Ghz
Memory: 1011.5MB
NVidia GeForce FX 5500
120GB Hard Drive
Ubuntu 7.04 (feisty)
I'm running Beryl window manager, Avant window manager, screenlets-tray.

[/SIZE]

---

### Post by alex_anthony on 2007-07-04
cant really solve your problem, but what icon set is that?

---

### Post by nehuenmingote on 2007-07-04
[SIZE="3"]> **alex_anthony said:**
> cant really solve your problem, but what icon set is that?

Glass Icons from **gnome-look.org**
Here you go:
[http://www.gnome-look.org/content/show.php/Glass+Icons+Theme?content=32146]("http://www.gnome-look.org/content/show.php/Glass+Icons+Theme?content=32146")

[/SIZE]

---

### Post by imluxwhoru on 2007-07-04
Heh. That's funny. I struggled with the same problem today.... It was right after I did a apt-get dist-upgrade. I noticed it downloaded some new compiz updates. I wonder if that is what broke our machines....

Anyways, after I played around with it for a while I discerned that it was Emerald that caused the crash. So, I popped into a terminal and:
```
sudo apt-get remove emerald
```
Then, if you already don't have it....
```
sudo apt-get install aquamarine
```
Then, restart X, and run beryl again. You should be good to go. 

Good luck!

---

### Post by nehuenmingote on 2007-07-04
:D
THANK YOU VERY MUCH **imluxwhoru**!!!
You solved my problem!

---

### Post by imluxwhoru on 2007-07-04
No problem. Always glad to help. 
But........
You maybe help me now?
-- [http://ubuntuforums.org/showthread.php?t=492438](http://ubuntuforums.org/showthread.php?t=492438)

*Grin*  :)

---

