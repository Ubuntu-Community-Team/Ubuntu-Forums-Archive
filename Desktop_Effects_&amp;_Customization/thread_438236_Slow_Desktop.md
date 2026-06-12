---
title: "Slow Desktop"
date: 2007-05-09
forum: Desktop Effects &amp; Customization
---

### Post by dnzz on 2007-05-09
After installing Feisty my desktop effects become too slow. For example when i try to minimize a window it minimizes in 3 frames. Opening a window is same. Also my favorite KDE game KAsteroids is very slow everything moves 5-10fps. 

Im using 1.0-9755 "nvidia" driver
Reinstalled it at least 10 times
Also tried "nvidia-glx-config enable" "nvidia-xconfig" commands
Using restricted drivers and not using it
Reinstalling Ubuntu 7.04

Any ideas?

by the way my computer: Asus A6Q00VC

intel centrino 1.86ghz cpu
2gb ram
geforce 6200 go

---

### Post by sowelie on 2007-05-09
The first thing I would check is for direct rendering.  Run this command in a terminal:
```
glxinfo | grep direct
```.

If the output says "Direct rendering: no" then that is the source of your problem.  You'll need to check your Xorg.0.log for errors.

---

### Post by dnzz on 2007-05-10
I run the command

It says: 
Direct rendering: Yes

---

### Post by dnzz on 2007-05-10
I've noticed something really interesting.

While copying something (a movie etc) to another place everything works fine but when it finishes everything goes slow again.

This is wierd...

---

### Post by dnzz on 2007-05-11
Changing kernel from generic to i386 solved the problem.

---

