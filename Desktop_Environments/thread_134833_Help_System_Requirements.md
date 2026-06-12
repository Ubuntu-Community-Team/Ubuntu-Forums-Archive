---
title: "Help: System Requirements"
date: 2006-02-22
forum: Desktop Environments
---

### Post by benblur4 on 2006-02-22
I have a fujitsu lifebook b142
I have upgraded the memory to about 90mb.
Is there any way I can install Ubuntu or Kubuntu on it?
I have read the minimal requirements for them but my computer RAM falls in the middle of the desktop and server setting:

--------------------------------------------------------------------------
Table 1 Recommended Minimum Requirements 

Install Type         RAM                          Hard Drive Space

Desktop              128 megabytes        2 gigabytes
  
Server                 64 megabytes          500 megabytes
--------------------------------------------------------------------------

Can I do it?  Thanks.

---

### Post by Denta on 2006-02-23
Take a look at xubuntu which is a lightweight desktop for a ubuntu server installation.
[https://wiki.ubuntu.com/Xubuntu](https://wiki.ubuntu.com/Xubuntu)

---

### Post by benblur4 on 2006-02-28
xubuntu is just what I needed.
I have installed it and every thing works fine...well... exept my screen resalution.
But any way thaks. this is a major leap for me.

---

### Post by az on 2006-02-28
Boot into recovery mode and run
dpkg-reconfigure xserver-xorg

Take the default for everything except color depth.  Pick 16-bit, and if it still is not what you want, pick 15-bit.

Then run
init 2

Ubuntu tries to use the maximum color depth, but that sometimes does not give you enouch of a desktop because it exhausts your video card memory (for really old cards, that is)

You can also install icewm and menu.  Log out of xfce and change your session to icewm.   It is faster than xfce.  Use synaptic (or the command line) to install the icewm and menu packages...

---

