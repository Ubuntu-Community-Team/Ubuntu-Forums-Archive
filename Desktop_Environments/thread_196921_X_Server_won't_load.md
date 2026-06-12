---
title: "X Server won't load"
date: 2006-06-15
forum: Desktop Environments
---

### Post by jflash on 2006-06-15
I know this is not directly related to Ubuntu, but I haven't gotten any response on the appropriate mailing list.

On Monday, I discovered Google Earth for Linux. I have always been a fan of Google Earth, and it has been one of the few things I have missed from Windows. Anyway, I downloaded and installed it with out a problem. However, there was a display issue once I got the program running. I checked the system requirements on Google's site. I knew I had X.org installed (the recommended program), but it wasn't working. Therefore, I tried the minimum program, XFree86. I installed that without any problems. 
The problem arose when I attempted to reboot after installing XFree86. Most of the bootup went fine. However, once it got to the point where the login screen should show, I got an error saying that my X server couldn't be loaded and as a result GDM couldn't be loaded. It gave me an option to view the output from my X server, which turned out to be a log file (which I am attaching). For what it's worth, after a few seconds, the error would appear in the background and the command line interface with the login prompt would appear in the foreground. After a little experimenting, I found that I could get Ubuntu to load correctly when booting into recovery mode and selecting failsafe GNOME in the login window. I tried a few times further and still no luck. At the advice of someone on the XFree86 mailing list, I ran the startx command at the command prompt. This helped not at all. What it did do was take me to a different screen, which had a dotted gray background and three different-sized boxes with the command prompt in them. 
Basically, what I am needing is to either a)remove XFree86 and revert the changes it made, or b)fix these problems. If anyone can help, please let me know. As I said, I am attaching the log file for the program. I can provide just about anything else necessary. Thanks!

---

### Post by jflash on 2006-06-16
Could someone please help me with this? I leave for vacation tomorrow and would like to have this worked out before I leave.

---

### Post by uruahv on 2006-06-16
Try "sudo dpkg-reconfigure xserver-xorg".

---

### Post by jflash on 2006-06-16
I tried it and went through the configuration with no problems, but it still dosen't work. Anything else?

---

### Post by ayoli on 2006-06-16
your log file says that Xfree86 server could not find the config file, and use a built-in conf.
Does your conf file have the right name, emplacement, perms ?

---

### Post by jflash on 2006-06-16
I have to admit I'm not sure. I could check if someone could tell me what those are.

---

### Post by ayoli on 2006-06-17
As far i renember, it must be /etc/X11/XF86Config for XFree86.

---

### Post by jflash on 2006-06-18
I am currently on vacation at the moment and won't be back to my computer until Saturday at the earliest. I'll try it then. Thanks!

---

