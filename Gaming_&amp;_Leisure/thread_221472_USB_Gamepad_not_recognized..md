---
title: "USB Gamepad not recognized."
date: 2006-07-23
forum: Gaming &amp; Leisure
---

### Post by Sarteck on 2006-07-23
I'm not sure if this should go in another section (if so, just have a Mod move it, but please lemme know about it, heh).

I'm still fairly new to Linux in general and very new to Ubuntu in particular.  I've been wanting to play my old PSX games on my computer, since I can't save them to PS2 memory cards. XD

Anyways, I've been trying to install and configure ePSXe for Linux using a tutorial I came across (a bit outdated, but still accurate, and can be found here: [http://terror.snm-hgkz.ch/gaming/linux/epsxe_howto/](http://terror.snm-hgkz.ch/gaming/linux/epsxe_howto/) ).  Other than using the updated plugins, I've not changed anything in that tutorial, and all was going well, until (and finally I get to my problem, heh)...

When I tried to load the **hid** module using modprobe, it gave me this error: "FATAL: Module hid not found."

My question is this...  Is there any way I can install a module short of re-compiling the kernel?  I mean, that's what the whole point of modules is, right?  That you can do stuff without having to rebuild your kernel?  Heh.

Thanks in advance for any advice.





**EDIT**:  OMG, I am so stupid...  After searching these forums, I found the answer.  For anyone who stumbles across this problem and is as much of an idiot as me, use **modprobe usbhid** instead of plain old "hid".  >.<

---

