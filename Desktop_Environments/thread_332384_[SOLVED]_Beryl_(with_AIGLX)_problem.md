---
title: "[SOLVED] Beryl (with AIGLX) problem"
date: 2007-01-06
forum: Desktop Environments
---

### Post by Interestedinthepenguin on 2007-01-06
I'm having a problem with running beryl on my laptop (Dell Inspiron B130). :neutral:  

When I type 'beryl-manager' into the terminal, this is what I get:

libGL warning: 3D driver claims to not support visual 0x4b


I see the beryl icon on the taskbar, but when I go to 'Select Window Manager' and click beryl, the titlebars on my windows disappear, and the beryl option (under 'Select Window Manager') isn't selected.  

This is what the terminal displays after I select beryl as my window manager:  

XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: symbol lookup error: beryl: undefined symbol:  
XCompositeGetOverlayWindow

Also:  I have emerald and emerald-themes installed, but the 'Reload Window Decorator' and 'Select Window Decorator' options are dimmed out.  

:???:

---

### Post by ComplexNumber on 2007-01-06
did you follow [these]("http://wiki.beryl-project.org/wiki/Install/Ubuntu") instructions?

---

### Post by Interestedinthepenguin on 2007-01-06
Yes.

...but I didn't install the svn snapshots.  Are those required?:-?

---

### Post by kurgan78 on 2007-01-06
I just finished setting up Beryl for the first time on my Dell Latitude D620 laptop, and I had the same problem as you. Follow the instructions in that link above carefully... and read the troubleshooting tip at the bottom of the page. I had to add in the "Extensions" section in my xorg.conf file, as well as a couple of other recommended options for my nVidia card. Although, those didn't fix the problem, changing default color depth from 16 to 24 in xorg.conf did the trick.

---

### Post by Interestedinthepenguin on 2007-01-06
Thanks for your help, guys.  

I'm trying to follow the directions again, but I'm hung up right here: 

...(depends on your graphic chip): (IF there is no Option "XAANoOffscreenPixmaps". Add it! for 855GM)

Section "Device"
Identifier "Intel Corporation Intel Default Card"
Driver "i810"
Option "XAANoOffscreenPixmaps"
BusID "PCI:0:2:0&#8243;
EndSection
--------------------------------------

My chipset (or whatever it is) isn't 855GM; my xorg.conf file says "Intel Corporation Mobile 915GM/GMS/910GML Express".  

I don't know what to add.:confused:

---

### Post by Interestedinthepenguin on 2007-01-07
*sigh*

Still no luck.  

I've followed the guide, I don't know how many times, and still can't get it working.](*,) 

**Note:**  My Ubuntu laptop has no internet access.:-?  ...but I do have the required packages.

---

### Post by mesamunefire on 2007-05-11
I have the same type of laptop as you do, a Dell b130 and if you download and install the latest ubuntu, you can use beryl without any problems. My computer is right now using it as I write. Its cool I have blue flames burn everytime I close a window (hehe).
Also its really easy to install beryl. Just go to aplications->add/remove
type in beryl (make sure you have all aplications set up) and you get...beryl! its really easy to install and you dont have to do a thing. 

Also, wireless now works. That made the difference between using windows or ubuntu for this laptop.

---

