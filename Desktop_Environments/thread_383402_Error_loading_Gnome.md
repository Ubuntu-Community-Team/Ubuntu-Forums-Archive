---
title: "Error loading Gnome"
date: 2007-03-13
forum: Desktop Environments
---

### Post by rennen01 on 2007-03-13
Any advice you can give me will help.

I installed conky and placed it in "Startup" Items.  I also installed a gstreamer package that may have caused this error.

Can anyone tell me to how to remove Startup Items from the Terminal? Also to check what that last package I installed was?

Thanks in advance.

---

### Post by rennen01 on 2007-03-13
Anyone?

I can start into KDE.  I will probably try to take that conky out of the Startup Items from KDE.  It almost seems like each Desktop Environment is totally independent since KDE will start with no problem.

I will post more info when I get home later.

---

### Post by rennen01 on 2007-03-13
:bump:

---

### Post by rennen01 on 2007-03-13
Booting into Recovery Console worked!

sudo dpkg-reconfigure xserver-xorg was the cure :)

---

### Post by rennen01 on 2007-03-13
Had to re-install latest NVIDIA Drivers

[http://www.ubuntuforums.org/showthread.php?t=336412&highlight=HOWTO%3A+Nvidia](http://www.ubuntuforums.org/showthread.php?t=336412&highlight=HOWTO%3A+Nvidia)

---

