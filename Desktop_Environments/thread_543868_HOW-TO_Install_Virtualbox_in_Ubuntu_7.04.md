---
title: "HOW-TO: Install Virtualbox in Ubuntu 7.04"
date: 2007-09-05
forum: Desktop Environments
---

### Post by MadMac on 2007-09-05
This worked for me, hopefully it will work for others.  :)

1. Edit /etc/apt/sources.list (in terminal enter: sudo gedit /etc/apt/sources.list), then copy and paste this at the end of the file:

		deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) feisty non-free


2. Reboot.  (System, **not** using alt-backspace.)


3. Open a terminal and type:  sudo apt-get install virtualbox


Then just answer the questions that pop up (I went with the defaults) and it's there and ready to run.

Hopes this helps someone in need!

---

### Post by dandandan on 2007-09-05
u dont need to reboot. apt-get update will do the trick.

---

### Post by MadMac on 2007-09-07
> **dandandan said:**
> u dont need to reboot. apt-get update will do the trick.

Okay.  All I know is that it took a system reboot to make it work for me.

Thanks!

---

### Post by yabbadabbadont on 2007-09-07
This is a duplicate of: 

[http://ubuntuforums.org/showthread.php?t=340113](http://ubuntuforums.org/showthread.php?t=340113)

---

