---
title: "Cannot Enable Desktop Effects -- Graphics Card Problem?"
date: 2008-01-04
forum: Desktop Effects &amp; Customization
---

### Post by ademel on 2008-01-04
Hi. When I try to run compiz, it tells me "Desktop Effects Could Not Be Enabled." I have a Sony Vaio VGN-CR190 laptop and the graphics card I am using is:

VGA Compatible Controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
PCI ID: 8086:2a02

As per advice elsewhere on the forum, I am running the fglrx drivers and have enabled xserver-xgl. However, this still has not made compiz work. When I type compiz into terminal, this is what I get:

Checking for Xgl: present.
Checking for nVidia: not present.
Checking for Xgl: present.
Enabling Xgl with fglrx ATi drivers. . .
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: Support for non power of two textures missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: no manageable screens found on display :1.0

Unfortunately, I am a complete linux newbie and don't really know what to make of this. Ideas? Any help is greatly appreciated.

---

### Post by t3hi3x on 2008-01-04
I know that fglrx is an ATI driver, not an Intel driver. Have you tried going to

```
System>>Administration>>Restricted Drivers

```

 to see if there is a 3D driver for intel cards in the repositories? If so that would be the easiest way to install them.

I'm surprised your xserver even runs with those drivers going. Let us know if there are drivers.

---

### Post by ademel on 2008-01-04
I've tried -- when I go to the Restricted Drivers Manager, it tells me "Your hardware does not need any restricted drivers." :confused:

---

### Post by t3hi3x on 2008-01-04
Can you post your xorg.conf file?

---

### Post by t3hi3x on 2008-01-04
Posted from another user with that GFX card:

> 
Sorry, I had a irritating description in the wiki.

Simply do the following:
Code:

sudo echo "SKIP_CHECKS=yes" >>/etc/compizconfig/config

Then check in the /etc/X11/xorg.conf file, that the driver for your graphic card is the intel one.

The entry should look similar to this example:
Code:

Section "Identifier"
  Identifier  "A name for the card
  Driver     "intel"
  ...
EndSection

and then try to enable compiz.

The biggest thing with the xorg file is having the "intel" part. This lets it use the intel drivers. I dont know a ton about the intel drivers specifically, but I have had some experience with ATI and nVidia's.

See what doing those two things do.

---

### Post by ademel on 2008-01-04
Thanks **t3hi3x**! That solved my problem :)

---

