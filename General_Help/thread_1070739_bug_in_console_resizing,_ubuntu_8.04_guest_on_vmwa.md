---
title: "bug in console resizing, ubuntu 8.04 guest on vmware 2.0.0 on Windows XP"
date: 2009-02-15
forum: General Help
---

### Post by supernatent on 2009-02-15
Hi, If anyone has a solution or at least a better handle on what's going on here, I'd love to hear about it. I think this is vmware-tools on ubuntu issue:

Software: ubuntu 8.04 as guest of vmware 2.0.0 (free version) on Windows XP (all 32bit)

Problem: broken automatic resizing of desktop to arbitrary resolution to match console.

Workaround 1: From vmware server home page, start the ubuntu virtual machine, but DON'T open a console right away, wait long enough for ubuntu to fully load (note: I have set ubuntu to automatically log in a user -- no gdm login required). Now open a console and console resizing works.

Workaround 2: If I start the console while ubuntu is loading (not heeding the advice of workaround 1), I find that console resizing doesn't work. To get it working, I put in a usb drive, load it into the ubuntu virtual machine via the vmware server home page, and voila console resizing suddenly works.

I think workaround 1 works because you wait until vmware-user (which is started as part of the user's session) is running on the ubuntu guest **before** starting the console. And workaround 2 I'm guessing works by somehow reinitializing the console, whence it notices vmware-user is running.

Other things I checked for: 
* I looked at lsmod before and after using workaround 2 (usb drive) and the only new module was libusual. Modprobe libusual didn't fix the problem.
* Likewise I looked for winXP services that were started as a result of workaround 2. Nothing.
* Obviously I tried killing and restarting vmware-user, to no avail. 

Thanks in advance.
Nathan

P.S. My ubuntu 8.10 virtual machine also has this problem, and the above workarounds don't work! But 8.10 is still really new.

---

