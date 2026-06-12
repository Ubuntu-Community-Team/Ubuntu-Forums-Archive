---
title: "xorg security update then ati driver stop working"
date: 2005-09-12
forum: Desktop Environments
---

### Post by jlx on 2005-09-12
Hi everyone
Today I updated my system and Synaptic downloaded many packets. There was a security update for xorg and mesa and all that stuff. When I reset the computer I checked the ati icon and the drivers loaded was from mesa and not from Ati. Before this update I have ati drivers working perfectly.
I've recomplied the module against the new version, doing all the steps again and couldn't be able to get ati drivers working.
Please, someone has had the same problem? a little help?
Thank you very much.

---

### Post by mlomker on 2005-09-12
I'd recommend deleting everything and trying again.  Look at [this thread.](http://www.ubuntuforums.org/showthread.php?t=64286)

---

### Post by jlx on 2005-09-12
Thanks a lot. You were right.  I had to download again the driver and install it to generete the right Makefile for the new xorg version. I also use the xorg.conf generator you recommend in another post. The only diference is that I have now 
UseInternalAGPagart=yes  
Should I leave that way? Do you know the difference?
Thanks again.

---

### Post by rafakl on 2005-09-12
Thats why i still dont want to update my system.

 :razz:

---

### Post by jlx on 2005-09-13
oh, come on. Yo get a lot of fun fixing things. Your self esteem go ups, you feel much younger and your skin gets more soft. It's a great exercise.

---

### Post by mlomker on 2005-09-13
[QUOTE=jlx]UseInternalAGPagart=yes  [/QUOTE]

It actually doesn't matter how you set it because the driver will use the internal AGP support.  The problem is that Ubuntu has it built into the kernel and you cannot disable it---unless you want to build your own custom kernel. 

ATI says that their version is faster than the kernel's.

---

