---
title: "Games not appearing after being installed."
date: 2006-08-13
forum: Gaming &amp; Leisure
---

### Post by Cartwheels4amile on 2006-08-13
I wanted to try a few linux games, so I went ahead and installed Trigger, tuxkart, and xracer. Unfortunately, after Synaptic finished the install, only Trigger showed up under Applications>Games, and even then, when I click on it, it fails to start.:confused:  I'm running Xubuntu, so my desktop environment is Xfce, if that makes a difference.

Thanks.

---

### Post by Perfect Storm on 2006-08-13
Try start via command eg.

```

trigger
```

etc.

---

### Post by Cartwheels4amile on 2006-08-13
here's what i get in terminal when trigger fails to launch:


will@will-laptop:~$ trigger
Trigger init
Build: 0.5.2 on May 11 2006 at 02:48:35
Initialising PhysFS
Set writable user directory to "/home/will/"
Reset writable user directory to "/home/will/.trigger"
Application base directory "/usr/games/"
Main game data directory datadir="/usr/share/trigger-data"
Loading game configuration
Initialising SDL
Create window and set video mode
Failed to create window or set video mode
SDL error: Couldn't find matching GLX visual
Try changing your video settings in data/trigger.config

---

### Post by Perfect Storm on 2006-08-13
Did you remember to install the 3D acc driver for your graphic card?

---

### Post by Cartwheels4amile on 2006-08-13
I'm running a Toshiba Portege 7140ct... the video card is a Trident CyberBlade e4-128. Being really new to linux (just a week or so) I really have no idea what I'm doing. If needed, I'll ask more in Hardware Support.

---

### Post by Perfect Storm on 2006-08-13
Heh, you'll better do ;) Havn't heard that brand before.

---

