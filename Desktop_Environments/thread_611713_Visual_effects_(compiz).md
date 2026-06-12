---
title: "Visual effects (compiz)"
date: 2007-11-13
forum: Desktop Environments
---

### Post by oamster on 2007-11-13
I've searched around and found nothing.

Whenever I try to enable any visual effects it gives me this:

 The Composite extension is not available


What does that mean? I have no idea... Any suggestions?

---

### Post by oamster on 2007-11-13
When I run compiz inthe terminal I get the following:

> oam@oam-laptop:~$ compiz
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
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: No composite extension

(gtk-window-decorator:5731): Gdk-WARNING **: Using Cairo rendering requires the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(gtk-window-decorator:5731): Gdk-WARNING **: Using Cairo rendering requires the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap



Also I just read that my driver isn't stable enough. I have the ATI Radeon XPRESS 200M 5955 with the fglrx driver.

Is this the best driver out for my GPU? Or would you recommend a better driver?

Thanks for any help.

---

### Post by oamster on 2007-11-13
Wow I finally got it to work!  If anyone else has the same problem just run this:

> sudo apt-get install xserver-xgl
 

Then press ctrl+alt+backspace to relog!

---

### Post by stuffelse on 2007-12-30
Worked for me too! FINALLY!

I've got a Radeon Xpress 200M, process was to enable the ATI restricted driver and run the xserver-xgl bit above, and I've finally got the extra special visual effects! =D>

thanks to oamster for actually posting results!

---

### Post by jeyaganesh on 2007-12-30
Hello Oamster,
Thank you very much. Your suggestion solved the problem in a second. Hats off!

---

