---
title: "File permissions..."
date: 2008-12-21
forum: General Help
---

### Post by dan_the_man on 2008-12-21
Hi guys, 

Linux noob here..sorry.

Just installed ubuntu 8.10 on my system and dont seem to be able to use my second monitor. Apparently this can be solved by editing xorg.conf (/etc/X11/xorg.conf).

The problem I'm having is logging in as root in order to change the mofo.

When I opened it strait from its file directory I cant save it as I dont have the correct permissions. 

When I opened it in terminal with the command 'root@dan-desktop:/home/dan# sudo gedit /etc/x11/xorg.conf' a blanc text editor file appears..

---

### Post by taurus on 2008-12-21
It should be capital X, not x11.

```
gksudo gedit /etc/X11/xorg.conf
```
By the way, you don't need to log in as root to edit it.  Just use sudo/gksudo and if you log in as root, no need to include the sudo in front.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by sisco311 on 2008-12-21
linux is case sensitive.
```
gksu gedit /etc/**X**11/xorg.conf
```
for GUI applications use gksu or gksudo instead of sudo.

when you have a little time, please read:

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

and

[https://help.ubuntu.com/community/FilePermissions]("https://help.ubuntu.com/community/FilePermissions")

---

### Post by dan_the_man on 2008-12-24
Thanks guys, Ill give it a go this afternoon. Sorry about the slow replay.. few minor computer issues. 

Also thanks for the reading material, I didn't know where to start when it came to learning Linux :)

---

### Post by dan_the_man on 2008-12-31
Well I got the first problem sorted (thanks guys!)

Now onto the second issue :p

For some reason my primary monitor seems to be taking some of the properties of my secondary monitor, aka I cant expand windows to fit it and there seems to be a blank square at the bottom of screen 1..

I can only apologise for my ignorance!

[http://img168.imageshack.us/my.php?image=screenshotfb2.png](http://img168.imageshack.us/my.php?image=screenshotfb2.png)

---

### Post by dan_the_man on 2009-01-01
> **dan_the_man said:**
> Well I got the first problem sorted (thanks guys!)

Now onto the second issue :p

For some reason my primary monitor seems to be taking some of the properties of my secondary monitor, aka I cant expand windows to fit it and there seems to be a blank square at the bottom of screen 1..

I can only apologise for my ignorance!

[http://img168.imageshack.us/my.php?image=screenshotfb2.png](http://img168.imageshack.us/my.php?image=screenshotfb2.png)

Actually it appears to have fixed itself! Phew:D

Cheers anyway.

---

### Post by MaxIBoy on 2009-01-01
Yeah, usually when that happens it's because you're cloning the output.



Anyway, if your problem is solved, use the "thread tools" menu option to mark the thread as solved. That way, someone else can seek out solved threads if they have the same kind of question.

---

