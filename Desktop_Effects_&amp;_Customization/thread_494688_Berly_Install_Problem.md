---
title: "Berly Install Problem"
date: 2007-07-07
forum: Desktop Effects &amp; Customization
---

### Post by adamdavid123 on 2007-07-07
I wanted to install beryl on ubuntu. 

I enabled the desktop effects(which is great!)

and then followed a tutorial from a website.

I got as far as this 

> Find the section labelled “Module” and make sure these three items are there. You’ll probably have the dri and glx entries but double check.
Load “dri”
Load “dbe”
Load “glx”

Now skip down to where it says “Device”. This will have some info about your graphics card. Add this line to this section just below “BusID”
Option “XAANoOffscreenPixmaps”

One more thing to change. Skip down to the very bottom and make sure these lines are present. If they’re not there, paste them in.
Section “DRI”
Mode 0666
EndSection
Section “Extensions”
Option “Composite” “Enable”
EndSection

Then i saved it and ctrl-alt-backspace and an error came up something about x, I can no longer get into ubuntu and everytime i boot the pc up i get the error and then to a 'dos' type screen with text.

It looks like i am in the recovery mode(as i have been there before) What can i do to rebuild all the files i edited?


I have tried with beryl before and no luck. But if i can rebuild the files as they were from the installation of ubuntu i will give it ago

(intel onboard graphics)

Thanks.

---

### Post by dwebb86 on 2007-07-07
if you get the blue screen of X....
the only way I know of to fix your wrongs is to hit ALT+F1 and log in to your account, then use **sudo dpkg-reconfigure xserver-xorg** and reconfigure your xorg.conf from there.
it can be a pain in the *** (I'm going through it now) but that's how you get back in. Also, I'm pretty sure you're supposed to remove the section on DRI, not add it, that might be your problem, though I'm not sure.

---

### Post by adamdavid123 on 2007-07-07
well, i went through. Just yes to everything. I dont know my card came or anything like that. Still didnt sort antthing.

I dont know what to change :S any ideas?

---

### Post by adamdavid123 on 2007-07-07
X server Driver

By defualt voodoo(tried that last time)
List

amp
ark
ati
chips
cirrus
cyrix
fbdev
glint
i128
i740
i810
imstt
mga
neo magic
newport
nsc
nv
rendition
s3
s3virge
savage
siliconmotion
sis
sisusb
tdfx
trident
tseng
vesa
vga
via
vmware
voodoo

I will choose vga seen as it is the one i have heard of :p

Then we get to another section. Brb though, 



Generic Video Card Intel i915
dont know. So i will just ok.


Video Card's bus identifier
PCI:0:2:0
Not sure here, so okay, Its onboard :\

Amount of memory used by the video card
Blank :confused: what do i put?
okay


Right the rest is about mouse/keyboard and i just okayed as it all seemed fine

---

