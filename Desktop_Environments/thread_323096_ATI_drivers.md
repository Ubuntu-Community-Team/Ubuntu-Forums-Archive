---
title: "ATI drivers"
date: 2006-12-21
forum: Desktop Environments
---

### Post by huviduc on 2006-12-21
i am having trouble trying to get my ATI Radeon 200m driver updated to the 3D driver. i want to try to install compiz but i can not seem to get 3D rendering to work. i downloaded the driver from their site, but i get this error when trying to install:

Could not open the file /home/huviduc/ati-driver-installer-8.26.18-x86.run.
gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

I tried following this and a few others to get it to work, and it doesnt seem to do it either. can anyone help me out a bit?

---

### Post by mrunion on 2006-12-21
Do a search on the forum.  The latest version that should be working is 8.32.5.  Try this link:

[http://www.ubuntuforums.org/showthread.php?p=1884265#post1884265](http://www.ubuntuforums.org/showthread.php?p=1884265#post1884265)

---

### Post by huviduc on 2006-12-21
ok, i think i have it installed, but i get this error when checking to see if direct rendering is working:

huviduc@huviduc-laptop:~$ glxinfo | grep rendering
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No

---

