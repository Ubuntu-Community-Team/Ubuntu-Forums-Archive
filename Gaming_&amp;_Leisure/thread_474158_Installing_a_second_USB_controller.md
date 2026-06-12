---
title: "Installing a second USB controller"
date: 2007-06-14
forum: Gaming &amp; Leisure
---

### Post by richardwad1 on 2007-06-14
I'm new to linux, so I'm having a little trouble configuring things the way they shoudl be. I igot one of my usb oads working with this tutorial 

[http://ubuntuforums.org/showthread.php?t=297361&highlight=playstation+gamepad](http://ubuntuforums.org/showthread.php?t=297361&highlight=playstation+gamepad)

It works great! It says to install a second pad all I have to do is:

tweak the script a bit if you want two or more joysticks at the same time (you’ll need another mknod line for js1, and you’ll need to make another symlink from /dev/input/js1 to /dev/js1).

....and that is my problem. I have no idea what that means.

Can someone help me out with that? Preferably, what I need to type to do it. Any help would be greatly appreciated.

Other than that, Ubuntu has been amazing.

---

### Post by Tesiph on 2007-06-15
Ok, type
```
sudo gedit /etc/init.d/joystick
```
to get the file back you just created, then just add
```
mknod input/js1 c 13 0
ln -s input/js1 js1
``` just above 'modprobe joydev'.
Just repeat that (with js2,3,4,5..) for more controllers.

BTW, have you read the second post of the thread you linked to?

---

### Post by richardwad1 on 2007-06-16
I tried this...iIt sets the controller up in my dev/input folder, but it still isn't detecting the second controller.

---

