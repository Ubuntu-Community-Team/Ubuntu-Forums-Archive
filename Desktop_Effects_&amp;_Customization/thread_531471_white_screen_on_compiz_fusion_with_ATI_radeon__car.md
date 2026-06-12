---
title: "white screen on compiz fusion with ATI radeon  card"
date: 2007-08-21
forum: Desktop Effects &amp; Customization
---

### Post by palermo99 on 2007-08-21
Hi, I have an ATI Radeon 9000 graphic card, and direct rendering is enabled thru the open source driver:

$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.
$ glxinfo | grep "direct rendering"
direct rendering: Yes

I have followed the following tutorial

[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

 to get compiz fusion installed, but when launching compiz --replace, I get my desktop split into two, on the left I get a white background(70% of the screen), on the right I get my usual background but moving windows around that section make a funny effect (my english is limited and I cannot describe what I see :P) . I can still see the open applications, and compiz effects are there

$ compiz --replace
Checking for Xgl: not present. 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking for nVidia: not present. 
Checking for Xgl: not present. 

I can post parts of my xorg if needed. Any help will be appreciated!!!

---

### Post by weizilla on 2007-09-12
> **palermo99 said:**
> Hi, I have an ATI Radeon 9000 graphic card, and direct rendering is enabled thru the open source driver:

$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.
$ glxinfo | grep "direct rendering"
direct rendering: Yes

I have followed the following tutorial

[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

 to get compiz fusion installed, but when launching compiz --replace, I get my desktop split into two, on the left I get a white background(70% of the screen), on the right I get my usual background but moving windows around that section make a funny effect (my english is limited and I cannot describe what I see :P) . I can still see the open applications, and compiz effects are there

$ compiz --replace
Checking for Xgl: not present. 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking for nVidia: not present. 
Checking for Xgl: not present. 

I can post parts of my xorg if needed. Any help will be appreciated!!!

I am in the exact same situation as you are. I have the same hardware and same software installed and I experience the same exact problem. I hope someone has the solution for this or better yet.. you solved it already and can tell me how to fix it! :)

---

### Post by rivaxunil on 2007-09-23
i have a Nvidia 8600m GT and i was facing the same problem using well, mandriva 2008 RC2, this is what i did to solve it:

format the partition, and made a custom install sellecting the development package also

after intslallation done, i went do software management and installed the kernel-devel package laptop
something like that (sorry, im a noob)

then i installed the latest drivers from NVIDIA using as root sh NVIDIA... -k $(uname -r)
drivers installed...rebooted

went to 3D settings to enable compiz and installed mesademos, selecting compiz fusion in native support mode.

for last i edited xorg.conf and added on the last line after the  "composite" i added  "enable"

reboot...

OK! Compiz fusion in its glory

Note: i have read somewhere that nvidia-glx was replaced by nvidia settings....so don't kick your head of trying to figure why you dont have nvidia-glx if you have nvidia settings ( maybe it works similar with ati, i dunno)

well, finally... hope this helps someone

---

