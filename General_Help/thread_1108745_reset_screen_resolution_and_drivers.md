---
title: "reset screen resolution and drivers"
date: 2009-03-28
forum: General Help
---

### Post by stillgreener on 2009-03-28
hi,
so very new to linux and just installed Ubuntu for the first time.  I am setting up a htmc and was adjusting the screen resolution when I had the great idea to see what the screen resolution "off" was and it did indeed turn it off. how do I reset?  :confused:

and also I have a gigabyte GA-MA78GPm-UD2H  motherboard with integrated video.  the disk provided is for vista and no drivers on the gigabyte site.  is there anything I need to install?  the main purpose is to run Boxee and power a 42" lcd flat panel

thank you in advance!!

---

### Post by ViMMeD on 2009-03-28
Try loading the boot shell at startup through recovery mode and type the following:

```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure -phigh xserver-xorg

sudo /etc/init.d/gdm start
```

As for the chipset I'd have no idea seeing as I use Intel which comes pretty much installed with 8.10

---

### Post by stillgreener on 2009-03-28
still not working.

got into the root shell. 

the responses:

stopping GNOME display manager...

file; backup in /etc/xll/xorg.conf.20090328071711

when I hit reset, it went to the color background and in about 5 seconds went black?? then reset and still no joy...

thank you in advance!

---

### Post by stillgreener on 2009-03-28
no need to respond, I just reinstalled Ubuntu.

but I realize that selecting off was an idiot thing to do, but it raises a bigger issue that Boxee (and similar television convergence software) is going to be opening up the "floodgates" of all different levels of users coming into the Debian/ Ubuntu "family."  And these types of fixes need to be more "mainstream" (in my opinion). Couldn't imagine an Apple user being asked to go into root to fix a menu choice that was readily accessable...

I realize this is not the "thread" for this soapbox, but here it is...

thanks ViMMed!

rg

---

