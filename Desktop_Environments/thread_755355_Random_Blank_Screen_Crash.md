---
title: "Random Blank Screen Crash"
date: 2008-04-14
forum: Desktop Environments
---

### Post by Bobthegoldfish on 2008-04-14
I recently bought a new PC and wanted to put Ubuntu on it. I have the 32bit 7.10, the 64bit 7.10 and a copy of 64bit 8.04 beta.

I initially tried installing 64bit 7.10. Before forcing 1024x768x16, removing quiet and splash and adding nosplash, the LiveCD would get to the boot selection screen (LiveCD, Memtest, Boot from first hard drive) and when I pressed enter it would start loading vmlinuz and then reboot. After forcing the various items, it would load to the desktop.

Roughly half way through the installation to hard drive, the screen blanked and the hard drive light came on and stayed on. The screen acted as if it had been unplugged from the PC, cycling between the two inputs before turning off. I did the normal things (move the mouse, ctrl-alt-f1, ctrl-alt-f4, ctrl-alt-del) and nothing happened so I ended up hard rebooting the machine. This happened a few more times, with the blank screen happening randomly while using the LiveCD environment.

Thinking this might be a driver issue, I downloaded 64bit 8.04 beta and attempted to install that. After another crash I was able to install 8.04 and had rebooted into the new install to get updates and to switch on the nVidia restricted driver. I installed the restricted video driver and restarted/rebooted. Upon attempting to get the updates from the update manager it got about half way through before crashing again. The next time it downloaded all updates and I had managed to install something and copy roughly 15Gb worth of data to the hard drive before crashing again. I tried the 32bit 7.10 but that is following a similar pattern.

I have tried running Memtest and have gotten it to go through and pass five times. I have Windows XP 32bit installed on the machine and that has no problems at all, including playing a modern game (Portal) with no stutters or crashes, nothing like what has happened with the Ubuntu install.

Machine is as follows:
Intel Quad Core cpu
Gigabyte P35C-DS3R motherboard
4 Gb ram
8800gt nVidia video card
SATA Hard Drive and DVD-RW drive
620W power supply

Any ideas? I really want to use Ubuntu on this machine and already use it on another machine with very little problem.

---

### Post by Gen2ly on 2008-04-14
no, that sucks.  hmm, withproblems like these it's best to try the alternate livecd.  It's a differernt install process but will likely be more likely to put on the the hardware.

---

### Post by Bobthegoldfish on 2008-04-14
I have been able to put 8.04 onto the hardware; the problem is getting it to stay up and running.

---

### Post by Bobthegoldfish on 2008-04-21
*bump*
I'm assuming that it's a driver issue due to the fact that it happens with both the installed version and the livecd and that memtest doesn't report any errors.

---

### Post by rogbas on 2008-05-03
Hi dude, I have a similar configuration and I'm experiencing similar problems. My hardware configuration:

Gigabyte P35-DS3 Mobo
Core Quad Q6600 proc
4gb RAM Kingston
Seagate SATA HD
GE Force 8400 / 512mb

I already have a stable Windows XP SP2 installation working on this machine with no problems and the memory is OK as well. 

First I tried installing Ubuntu 8.04 Desktop 64bits edition, the installation went fine but from time to time I was getting random reboots. My initial suspect was that the NVIDIA GL driver was freezing, so I turned it off but the problem continued. 

Then I figured this was an issue with the 64bits edition and installed the Ubuntu Desktop 32bits edition, on this one the reboots were not so frequent but they are still happening.

Since our mobo has a relatively new Intel chipset I'm thinking this might be some compatibility problem with the linux kernel packaged with Ubuntu. I didn't try to recompile a new kernel yet. 

Anyone managed to solve this problem?

Regards,
   Rogerio Bastos

---

### Post by rogbas on 2008-05-04
Did a BIOS update and the problem was solved. I was using the F10 version and updated to F12, looks good now...

---

