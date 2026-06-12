---
title: "XFCE4 crash"
date: 2006-12-23
forum: Desktop Environments
---

### Post by fenomenoxp on 2006-12-23
Hi everyone! I've tried to install xfce4 on edgy (amd64). I used 
```
apt-get install xfce4
```
instead of 
```
apt-get install xubuntu-desktop
```
because of download size.
The problem is that when I log in XFce, It hangs up, showin a blinking Bug Buddy window (I can't read anything on the window, just the title). All I can do is Ctrl-Alt-Backspace and log back in kde/gnome. When I log in gnome, I get a report that *xfce4-panel" and "xfce4-session" have failed, but it gives no clue on why they have done so.
I have tried starting up xfce4-panel on gnome or kde, and it starts up, though it has no icons, just one button that does nothing (I get a tooltip when mouse is over it, saying it is not configured or something like that).
Any clues? Did I miss any importat package?
Thanks in advance

---

### Post by zek725 on 2006-12-24
> **fenomenoxp said:**
> Hi everyone! I've tried to install xfce4 on edgy (amd64). I used 
```
apt-get install xfce4
```
instead of 
```
apt-get install xubuntu-desktop
```
because of download size.
The problem is that when I log in XFce, It hangs up, showin a blinking Bug Buddy window (I can't read anything on the window, just the title). All I can do is Ctrl-Alt-Backspace and log back in kde/gnome. When I log in gnome, I get a report that *xfce4-panel" and "xfce4-session" have failed, but it gives no clue on why they have done so.
I have tried starting up xfce4-panel on gnome or kde, and it starts up, though it has no icons, just one button that does nothing (I get a tooltip when mouse is over it, saying it is not configured or something like that).
Any clues? Did I miss any importat package?
Thanks in advance

If you're concerned about lightweight, i think this might help. [http://www.ubuntuforums.org/showthread.php?t=206022](http://www.ubuntuforums.org/showthread.php?t=206022)

---

### Post by fenomenoxp on 2006-12-24
Well I just want to give a try to XFCE. I have seen that post and I've used some of the recommendations. 
I installed another package named xubuntu-default-settings and when I logged in, everything worked almost fine (I had to configure the panel manually). Anyway, next time I tried to log in, the bug happened again... Right now it's not working.
I'm trying to execute xfdesktop and xfce4-panel from kde (I know that the latter worked) and it is segfaulting.

---

