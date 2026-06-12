---
title: "GNOME Now Starts VERY Slowly..."
date: 2005-08-27
forum: Desktop Environments
---

### Post by lawtech on 2005-08-27
I tried the GISKnoppix LiveCD on my Ubuntu 5.04 installation. Now when I cold boot Ubuntu, there is a 3-5 MINUTE (!) delay between typing my username/password and seeing the GNOME Desktop. In between, the mouse works, but all I get is a blank tan screen. Once it comes up, everything seems to be in order. I notice no further delays.

The LiveCD (which uses KDE) obviously scrogged something. Can anybody give me a hint how to get my system back to its nice, fast performance?

I'm guessing the LiveCD somehow messed up the HW probe, but what to do next is a mystery to me.

Thanks in advance for any help.

Nick

---

### Post by lawtech on 2005-09-20
I still don't know why the Gnome Desktop takes so long to load after I provide my user name and password, but I've found something that at least helps:

If I use CTRL-ALT-F1 to get a character terminal, then from su, kill the two gdm tasks and the X task, then issue the gdm command, the Desktop pops up immediately in CTRL-ALT-F7 (where it was trying before). Don't know why this helps, but it beats waiting five minutes.

I'd love to hear an explanation of this. Anybody?

Better yet, I'd REALLY love to hear a permanent fix!

---

### Post by lee_connell on 2005-09-20
I'm interested also.

---

### Post by Xiata on 2005-09-21
[QUOTE=lawtech]I still don't know why the Gnome Desktop takes so long to load after I provide my user name and password, but I've found something that at least helps:

If I use CTRL-ALT-F1 to get a character terminal, then from su, kill the two gdm tasks and the X task, then issue the gdm command, the Desktop pops up immediately in CTRL-ALT-F7 (where it was trying before). Don't know why this helps, but it beats waiting five minutes.

I'd love to hear an explanation of this. Anybody?

Better yet, I'd REALLY love to hear a permanent fix![/QUOTE]
 Uhh... there really should only be one running gdm task...
gdm-binary i believe. I use KDM though, since i use kde primarily

---

### Post by lawtech on 2005-09-23
Here's what's running. What now?

lawtech@ubuntu:~ $ ps xa | grep gdm
 8143 ?        Ss     0:00 gdm
 8144 ?        S      0:00 gdm
 8149 ?        S     25:08 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
 6853 pts/0    R+     0:00 grep gdm
lawtech@ubuntu:~ $

---

