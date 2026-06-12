---
title: "dual monitors in gnome?"
date: 2005-07-17
forum: Desktop Environments
---

### Post by cyg on 2005-07-17
Hi
I was using redhat fc3 before I switched to ubuntu, and it had a built in gui that could set up multiple monitors.  I wish ubuntu had this.  Is there any software available to do this?  Or could someone tell me where to change things to make both monitors active?
what I have:
NV17 Geforce4 mx 440-se
Rage 128 PF/PRO AGP 4x TMDS

When it boots it starts text on the nvidia then goes to the rage card for graphical.
thanks for any help you can offer
-cyg

---

### Post by netrattler on 2005-07-17
Here is an article that explains how to setup dual monitors with Xinerama, I've used it with ubuntu before with no problems.

[http://docs.linux.com/article.pl?sid=03/10/05/025207&tid=](http://docs.linux.com/article.pl?sid=03/10/05/025207&tid=)

Joe

---

### Post by cyg on 2005-07-17
My XF86config-4 file has no information listed within it.  How can i refresh it or whatever I need to do so that I may add information to it?
thanks

---

### Post by Nikola Kasabov on 2005-07-17
If you had nvidia drivers installed then xinerama is disabled and you must use TwinView provided with their (nvidia) drivers. If the drivers are installed (nvidia-glx package) then there must be manual for twinview and drivers in general here - /usr/share/doc/nvidia-glx/readme.gz

And btw you must look in /etc/X11/xorg.conf not XF86config-4 - it is for other distros

---

