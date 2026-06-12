---
title: "How can I load an os using command line in cli?"
date: 2016-04-10
forum: Desktop Environments
---

### Post by bob120 on 2016-04-10
Solved.
Edit: wrong question, wrong forum.

---

### Post by TheFu on 2016-04-10
I've re-re-read the post and still don't know what you want. Sorry.  

If you have a chromebook, normal install instructions don't usually work.  Every model chromebook is different and need specialized installation instructions which usually begins with opening the case and removing a screw.

If you post the exact vendor AND model of each device, perhaps someone with the same hw will reply?

All discussions about 15.04 aren't helpful as that OS is not supported any longer.

If you have a command prompt, it is possible to load the GUI packages - depends on which GUI you want.  Which is best for your needs depends on the specific hardware.  On older computers, LXDE is probably best.  If you have a hot $200 GPU, then normal Unity/Ubuntu is fine for many people.

Not sure what a "timer battery" is or how those matter to any computer.  CMOS battery perhaps?

dots/star?
Correct fonts?
You've lost me completely.  I'm probably just stupid. Sorry.

---

### Post by grahammechanical on 2016-04-10
If you can switch to a command line using Ctrl+Alt+F2 then an OS has already loaded. It is called Linux. What is not loading is Ubuntu with its desktop environment, login screen & user interface.

Forget 15.04 that is out of life. It will no longer get security fixes. So, there is no point is us given advice about 15.04. And trying to advise on problems with 2 different machines is confusing. Just deal 
with one machine. 

Question: Does the Ubuntu 15.10 Try/Live session load? If it loads in a live session but not when it is installed then, in my mind it all points to the video drivers. The live session uses an open source video driver. But when we install and tick the box "Install third party software" we get a proprietary video driver. That is the difference between a live session and an install session.

Then there is the matter of what you call "my old computers." How old? It could be that the proprietary video drivers that come with Ubuntu 15.10 no longer support your old video adapters. It is the situation I am in. So, I install without ticking the box "Install third party software." And after I have a working desktop I decide if I need to use a proprietary video driver and I look in Additional Drivers for a legacy driver for my video adapter.

The Grub boot menu has an option called Advanced options for Ubuntu. That is a sub-menu and that sub-menu gives us options to load a Linux kernel with recovery mode. The recovery menu Resume option will load to a desktop using a fallback open source video driver. Or may be not. It is worth a try in these situations.

The recovery menu also has options to set up an internet connection (Network). If we have an ethernet connection to the router then the Network option will make use of that. Then we can go to Root - root shell prompt. And there is the Linux OS. And we can run commands. To get out of the root shell prompt type exit.

Regards.

---

### Post by buzzingrobot on 2016-04-10
Operating systems are launched by the machine's BIOS, which controls the machine when it starts up.  If all the hardware passes the checks the BIOS does, it passes control to the bootloader, which is located at a known location on the boot drive.  That bootloader then starts up the operating system.

In other words, you cannot install or "load" an operating system from the command line because no command line, or any other process, is available until the operating system launches.

If you're just trying to get Ubuntu reinstalled on those machines, burn an install image on that Chromebook, tell the target machine to boot from the DVD or USB stick, and do the install. If the laptops were previously running Ubuntu, and no parts have failed or been damaged or swapped out for something incompatibile, then doing a new install should be routine.

---

### Post by TheFu on 2016-04-10
Chromebook installs are not routine the first time and may never be routine. HW changes are always required, IME. Sometimes, it is impossible to install a normal Linux onto some models of Chromebooks.  For example, my toshiba CB35 will allow a normal Ubuntu 14.04 install, provided I don't enable whole disk encryption. If I do, it won't boot again and I have to start over from scratch by loading ChromeOS from recovery media first.  15.xx and 16.04 alpha/betas have never booted on this chromebook.  The 14.04 installation with encryption seems to go fine - it is the first boot post-install that never works - grub doesn't get run, so it doesn't look for the crypt'd partition, then LVM for the rest of the OS. OTOH, my Acer C720 almost became a normal laptop after the HW modifications and there weren't any issues loading any Linux that I tried with or without encryption (beyond the lack of ethernet drivers for the USB-GigE adapter I used).  My point is that chromebooks are not all normal PCs and don't just work with any install.

But I don't think the OP is trying to do anything with a chromebook based on #1 post.

Really need to pick 1 system and only work on that 1 in this thread. I'm not as young as I was yesterday, so confusion is common.

---

### Post by bob120 on 2016-04-10
edited.

---

### Post by bob120 on 2016-04-11
edit

---

### Post by bob120 on 2016-04-11
Solved.

---

