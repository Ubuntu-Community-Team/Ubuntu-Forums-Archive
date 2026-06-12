---
title: "Desktop Effects (nvidia-glx-new) causes a LOCKUP when laptop lis is closed"
date: 2008-08-27
forum: Desktop Environments
---

### Post by ichudov on 2008-08-27
I have a Acer laptop with a 64 bit version of Ubuntu Hardy. 

It works fine without "desktop effects". 
I tried to enable desktop effects. The OS installs the nvidia-glx-new proprietary driver. After that, the screen would work fine, with advanced features working, but the LAPTOP WOULD FREEZE AS SOON AS I CLOSE THE LID. 

After this, I would have to power it off and on again. 

Removing nvidia-glx-new and reverting to the open source drives removes visual effects and clears the problems. 

I am not really a fan of closed source anything and used to just badmouth this driver, but I want to ask here in the last chance hope that someone else found a solution to this. 

At the time of the crash, there is nothing in /var/log/messages or /var/log/syslog.

---

