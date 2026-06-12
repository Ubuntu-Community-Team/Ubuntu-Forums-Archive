---
title: "desktop effects not working"
date: 2009-04-12
forum: Desktop Environments
---

### Post by YOOHOO on 2009-04-12
I am running ubuntu 8.10 and I recently attempted to install flight gear.  It resulted in my hardware drivers being removed and now my desktop effects will not work. After reading through some of the other threads I tried: 

sudo dpkg-reconfigure -phigh xserver-xorg 

Unfortunately it didn't work. 

Your guidance is greatly appreciated.

---

### Post by overdrank on 2009-04-12
Hi and welcome. What is the model of the graphics card? You may also look at the FAQ link in my signature.

---

### Post by YOOHOO on 2009-04-13
> **overdrank said:**
> Hi and welcome. What is the model of the graphics card? You may also look at the FAQ link in my signature.
I have an Intel Mobile GM965/GL960 integrated Graphics Controller.

---

### Post by overdrank on 2009-04-13
> **YOOHOO said:**
> I have an Intel Mobile GM965/GL960 integrated Graphics Controller.

Ok then you may try and boot into recovery mode and use the xfix option to correct graphical issues.
I have seen many thread with issue on the intel graphics with Intrepid 8.10. I do not have the experience with the intel graphics on 8.10 though to help with this issue.

---

### Post by YOOHOO on 2009-04-18
Ok, I couldn't find a solution to this problem so I reloaded ubuntu.  I loaded all the software I had before, one at a time, to see what caused the issue.  When I loaded VM Ware server 2.0 it caused my desktop issues to come back.  I un-installed VM Ware but still had the desktop effects problems. I reloaded ubuntu yet again but this time tried KVM as my virtualization solution and my problem returned. It is worth noting that only my account had these problems my wife's account would allow her to enable all the desktop effects.

---

