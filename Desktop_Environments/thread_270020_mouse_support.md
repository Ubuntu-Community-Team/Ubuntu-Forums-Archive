---
title: "mouse support"
date: 2006-10-02
forum: Desktop Environments
---

### Post by grough on 2006-10-02
I've just installed a bare-bones gnome GUI on top of my dapper server install. This included the following packages:
 
xserver-xorg
xserver-core
gnome-core

Woo hoo! It works - but there is no response to mouse movement. Do I need any other packages for that?

Thanks

---

### Post by skymt on 2006-10-02
XOrg handles the mouse, so it should work. Can you post your /etc/X11/xorg.conf?

Also, if you compiled your own kernel, you may not have compiled some parts necessary for mouse support, especially if you have a USB mouse. That bit me quite a few times when I was using Gentoo.

---

### Post by grough on 2006-10-02
No luck with PS2, but I tried with a USB mouse and all's well. Thanks.

---

