---
title: "Permission Denied for xorg config"
date: 2006-04-09
forum: Desktop Environments
---

### Post by lonelypauly on 2006-04-09
**_/etc/X11/xorg.conf: Permission denied_**

this is the message i keep getting when trying to configure xorg...all i need to do is configure nvidia twinview.

---

### Post by aysiu on 2006-04-09
Try ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo gedit /etc/X11/xorg.conf
``` or ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nano /etc/X11/xorg.conf
``` or ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by lonelypauly on 2006-04-09
i rebooted and wasn't able to get to the desktop at all this time.  i got a message about the video config file is screwed up and it starts up the console or whatever for text commands.  im not a noobie to computers, but definately to linux, so i must have put something in the wrong place for my xorg config file.  oh well, i will just reformat...i want to try other distro's anyway because my sound doesn't work with ubuntu and i didn't get nvidia twinview to work either.

---

### Post by Afief on 2006-04-09
if you got a text screen(Terminal/bash) you can just recopy the backup files aysiu had you make:
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

having to use the Terminal is one of the thing that scares new users away, but after a while the terminal kinda becomes your favorite workplace, i do most of my work there and i'm stil a noob:D okay, sometimes i have to go back to the GUI because i don't know the commands:)

---

