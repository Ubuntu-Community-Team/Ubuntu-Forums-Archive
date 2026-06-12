---
title: "Black screen on boot"
date: 2006-06-01
forum: Desktop Environments
---

### Post by kalata on 2006-06-01
First of all here is what I know about the system
----
AMD Athlon 959Mhz (f6m4s2)
774MB RAM
ATI Radeon 9550 
SyncMaster713n monitor.
-----
On boot everything is fine until the "starting kernel" message. Then it gets black on the monitor (and flickering one the TV) and on the monitor I get the "Not supported resolution message" If I wait until gnome (or I guess the X) starts it appears again and it is working fine. If I kill the X - again I am in front of a black screen.:( 
I guess I have to change the some display mode. Can anyone help me fix that. ](*,)

---

### Post by kalata on 2006-06-03
some update... 
same is happening when I boot live cd 

the Information that I get from the monitor can be seen here:
[[IMG]http://img93.imageshack.us/img93/874/s25000722ve.th.jpg[/IMG]](http://img93.imageshack.us/my.php?image=s25000722ve.jpg)

I got some advice that it can be framebuffer device related and changing in /boot/grub/menu.lst   vga=XXX  to vga=normal  or even deleting it might help.
Unlucky for me that didn't have any effect at all. 

:(

---

