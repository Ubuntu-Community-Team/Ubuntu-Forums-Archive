---
title: "Complete Noob needs VNC help please."
date: 2006-01-15
forum: Desktop Environments
---

### Post by rugglez on 2006-01-15
Hi all, this is a great forum you have, and I am really starting to get into Ubuntu as an alternative to M$.

I am slowly getting my head aroung Ubuntu but am having some small problems.  I have tried searching the board but have found it very hard to find the answer to my question, hence this post.

My plans are to have my Ubuntu box sitting on the network as a file server, disc burner and media streamer which I currently do on a WinXP machine.  Ubuntu will need to run as a headless unit (no monitor, keyboard or mouse) which I will connect to over the network using my laptop (WinXP at the moment).  I did this with no effort at all on my XP server by using RealVNC Server on the server computer and RealVNC Viewer on my laptop.

So far on Ubuntu I have managed to connect 2 ways:-

NX Client (FreeNX) - Connects like Windows 'Remote Desktop Connection'  which is totally not what I want, as when I log off my lap-top, NX logs off Ubuntu too, meaning it is not doing anything stand-alone.

X11VNC - This is great as I can connect using RealVNC or other VNC software, but I have 1 HUGE problem.  I need to log on to the Ubuntu Box before I can connect using RealVNC which defeats the object of it.  This means I still have to have a monitor, keyboard and mouse to log on so I can use RealVNC remotely.  On WindowsXP I can use RealVNC as soon as the log-in screen appears meaning I can do everything remotely.


If you know a way I can log-on/off completely remotely using some type of VNC, PLEASE let me know.  Also, ultimately I am wanting to change my laptop to Linux too, so advise on how to do it on both Linux and WinXP would be most appreciated.

TIA

rugglez

---

### Post by Leigh on 2006-01-15
I use VNC heavily at work, but unfortunately, not with Linux boxes. The only suggestion I can make is to try the [VNC web site]("http://www.realvnc.com/faq.html"), but I'm guessing you've tried that route. Maybe if one of the clever people here could suggest a way to make VNC run as a background process....

---

### Post by az on 2006-01-15
[QUOTE=rugglez]Hi all, this is a great forum you have, and I am really starting to get into Ubuntu as an alternative to M$.

I am slowly getting my head aroung Ubuntu but am having some small problems.  I have tried searching the board but have found it very hard to find the answer to my question, hence this post.

My plans are to have my Ubuntu box sitting on the network as a file server, disc burner and media streamer which I currently do on a WinXP machine.  Ubuntu will need to run as a headless unit (no monitor, keyboard or mouse) which I will connect to over the network using my laptop (WinXP at the moment).  I did this with no effort at all on my XP server by using RealVNC Server on the server computer and RealVNC Viewer on my laptop.

So far on Ubuntu I have managed to connect 2 ways:-

NX Client (FreeNX) - Connects like Windows 'Remote Desktop Connection'  which is totally not what I want, as when I log off my lap-top, NX logs off Ubuntu too, meaning it is not doing anything stand-alone.

X11VNC - This is great as I can connect using RealVNC or other VNC software, but I have 1 HUGE problem.  I need to log on to the Ubuntu Box before I can connect using RealVNC which defeats the object of it.  This means I still have to have a monitor, keyboard and mouse to log on so I can use RealVNC remotely.  On WindowsXP I can use RealVNC as soon as the log-in screen appears meaning I can do everything remotely.


If you know a way I can log-on/off completely remotely using some type of VNC, PLEASE let me know.  Also, ultimately I am wanting to change my laptop to Linux too, so advise on how to do it on both Linux and WinXP would be most appreciated.

TIA

rugglez[/QUOTE]

System - Preferences - Remote desktop (Ubuntu ships with VNC out-of-the-box)
System - Administration - Login screen setup (Tell it to autologin a user of your choice automatically -  You share your desktop once it boots!)

---

### Post by yanik on 2006-01-15
how about this one?

[http://www.ubuntuforums.org/showthread.php?t=42941](http://www.ubuntuforums.org/showthread.php?t=42941)

---

