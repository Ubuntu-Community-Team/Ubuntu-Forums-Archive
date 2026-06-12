---
title: "Can't play games installed through Apt-get install"
date: 2007-08-12
forum: Gaming &amp; Leisure
---

### Post by Swarms on 2007-08-12
Games I have previously installed like Irrlamp, and games I install either through Add Remove or the terminal, I can't play.

For example, if I say sudo apt-get install lincity-ng, it finds , downloads and install it. But when I try to launch the game through the gnome menu it says:

Could not launch menu item
Failed to execute child process "lincity-ng" (No such file or directory)

If I try to write lincity-ng, it acts like I haven't installed it, it simply yabs about its not currently installed, type sudo apt-get install and so on.

What can I do about it?

It seems like its only games that are influenced, hence the placement.

---

### Post by Swarms on 2007-08-12
Bumpity bump

---

### Post by DoktorSeven on 2007-08-12
You're not running as root somehow are you?

Game launchers are put in /usr/games/ and normal users *should* have this in their PATH, but root does not.  From a prompt, do
**echo $PATH**
and see if /usr/games is missing for any reason.

---

### Post by Swarms on 2007-08-13
> bear@bear-desktop:~$ echo $PATH
/home/bear/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/opt/e17/bin

I guess not?

---

