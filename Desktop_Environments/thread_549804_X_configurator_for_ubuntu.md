---
title: "X configurator for ubuntu"
date: 2007-09-13
forum: Desktop Environments
---

### Post by zoffmann on 2007-09-13
Hi,

is there any good X configurator for ubuntu besides dpkg-reconfigure xserver-xorg.

That what I need is to set up screen resolutions.

best regards
:)

---

### Post by s26c.sayan on 2007-09-13
Easiest way :
Open up the file /etc/X11/xorg.conf in your favorite text editor as ROOT,  and edit!!

(Don't forget to keep a backup!!)

---

### Post by zoffmann on 2007-09-13
The second question:

How do I choose default resolution during the boot  in xorg.conf?

---

### Post by s26c.sayan on 2007-09-13
Scroll down in the file xorg.conf until you reach the section headed 
[B]Section "Screen"
[/B]Under this section, you should choose the correct '**Defaultdepth**'. For me it is '24'.
Then scroll further below to the **Sub section "Display"** corresponding to the default depth chosen. There keep all the resolutions you want, in descending order.

And don't forget the backup!!!

----------------
EDIT : You should also input the correct values for Horiz Sync & Vertical Refresh rates for your monitor in the section headed "Monitor"

---

### Post by zoffmann on 2007-09-13
I found "default depth" and corresponding resolutions.

 I want to set up resolution during the boot and login to 1024x768 ?

How do I do that?

---

### Post by s26c.sayan on 2007-09-13
Here is the relevant portion of MY xorg.conf. I use it to start off with a default resolution of 1024x768 :  [http://marchlinux.pastebin.com/dbb4d390](http://marchlinux.pastebin.com/dbb4d390)

Remember, you need to set up the correct refresh rate ranges for your monitor! This is VERY important!

---

