---
title: "Compiz Problem"
date: 2008-03-02
forum: Desktop Effects &amp; Customization
---

### Post by RupeDeLaRupe on 2008-03-02
Hi Everybody,
Just wondering if anyone can cast a light on rather a problem I've been having,
I've just installed Ubuntu 7.10, and was hoping to be able Compiz-Fusion up and running.
I installed the Restricted driver that was meant to work with my ATI Radeon X1550, then installed the stuff for Compiz.

It doesn't work! :mad: 
I read that if you put "SKIP_CHECKS=yes compiz" you get all of the errors that it's having; this is what i got: 

> Ubuntu-Desktop:~$ SKIP_CHECKS=yes compiz
Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald

(emerald:5973): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed
/usr/bin/compiz.real (core) - Fatal: No composite extension

Any ideas gratefully received!!

---

### Post by benerivo on 2008-03-02
The "Fatal: No composite extension" warning is something i have had myself. I fixed it by adding the composite extension to my /etc/X11/xorg.conf file. My card is nvidia and not ati, but there is some [guidance]("http://wiki.compiz-fusion.org/ATI_with_AIGLX") for how you do this if you need to.

---

