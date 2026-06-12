---
title: "driver for Realtek RTL8201CL"
date: 2009-03-21
forum: General Help
---

### Post by barryvanveen on 2009-03-21
Dear all,

After installing a new motherboard into my computer I've got an irritating problem. Everything works but when I plug in my internet-cable I get some kind of kernel panic. There's no warning or error but the screen freezes and none of my keys work (capslock is flashing). The only thing to do is reboot and leave the utp-cable out.

By searching the interwebs I finally fixed it for Windows XP (it's a dual boot). I had to install another kind of driver from Nvidia for my ethernet card. Because this worked on Windows I hoped to find some comparable driver for Ubuntu 8.04. 

My motherboard is a MSI K9N6PGM2-V which includes the Realtek RTL8201CL ethernet device. I couldn't really find the drivers on the Nvidia website. Maybe I need the Restricted Driver that I have come upon during previous Ubuntu installs. The problem is that I can't install it because my pc crashes before I can download it.

Can someone tell me how to find the right driver and how to install it? I have got a laptop (typing on it now) to download drivers so I can get them on my pc.


Thanks in advance!

Barry

---

### Post by barryvanveen on 2009-03-21
Eventually I found this driver: [http://www.nvidia.com/object/linux_nforce_1.0-0310.html]http://www.nvidia.com/object/linux_nforce_1.0-0310.html](http://www.nvidia.com/object/linux_nforce_1.0-0310.html]http://www.nvidia.com/object/linux_nforce_1.0-0310.html). I don't know if this would fix the problem (I think it would).

Problem is that I get a message saying that "no precompiled kernel interface was found to match my kernel" and that this means "the installer will need to compile a new kernel interface". When I press OK it gives an error saying that I don't have the libc header files installed which are needed for compiling. Offcourse I don't have these installed because I don't have a working internet connection. 

Is there any workaround for this problem? Can I download the libc header files (or build-essential package) on my laptop and install them on my pc?

---

