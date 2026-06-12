---
title: "XT850 XT Platinum Edition Drivers"
date: 2006-01-09
forum: General Help
---

### Post by Tuf on 2006-01-09
I have installed Kubuntu 5.10 Breezy several times in my attempt to get 3D acceleration enabled on my XT850 XT (ATI).  Everything works superbly until I get to this step.

Kubuntu fills just about all of needs for daily computing requirements and I would like to make the switch from Windows XP for at least 90% of my computing needs and if I can get 3D working I think I am there :D

I have tried every method documented here on these forums with no success. I have tried the method documented and linked to from the Gentoo Forums that involves hex editing the lib files.  

There are a couple of questions that I have that I cant find answers for.

1) Should I install the latest drivers from a clean install or should I updated to the 686-smp kernal before? (I have been updating before trying to install the drivers.)

2) Should install the drivers from within KDE or should I exited KDE first?  I am comfortable working from the command line as long as I can find the commands needed. (How do you exit completely out of KDE and how can you see exactly what is running and loaded?)

3.)From the ATI release notes for the latest driver;
In order to use the fglrx internal AGP support, you have to make sure that the kernel agpgart support is not active, i.e. it is not compiled into the kernel and the kernel modules are not loaded. If the fglrx kernel module detects that the kernel agpgart support is active, it will automatically use that even if its internal AGP support is requested in order to avoid conflicts that can cause problems under some circumstances.

How do I check that and how do I unloaded it if it is running?

4.) Again from the ATI release notes;

Version 2.6 kernels require a second kernel module in addition to agpgart, which should be named similar to the manufacturer of your motherboard AGP chipset. This error message should occur if the other agp module is not loaded.

This issue can be worked around as follows:

   A. First make sure that agpgart is loading properly.
   B. To find out which AGP controller your motherboard uses, issue the following command: lspci | grep AGP
   C. To find a list of AGP related kernel modules installed on your machine, issue the following command and look for a module (*.ko file) that suits your AGP Controller: ls /lib/modules/`uname -r`/kernel/drivers/char/agp
   D. Use the modprobe command (as root) to load the module. For example: On a motherboard using a VIA® AGP Controller, you would load the via-agp.ko using modprobe as follows (notice that the trailing.ko is omitted): modprobe via-agp

Check the modprobe manpage for more information on loading kernel modules.

   E. To verify that the AGP module is already loaded, run lsmod as root. With the X server running and the connection established, the usage count of this module must be greater than zero. 

If you cannot find a suitable agp module for your motherboard, then you may want to upgrade to the latest version of the Linux kernel, or check your motherboard manufacturer's website for more information.

Again this something I havent seen addressed anywhere unless the commands used do in fact do this automatically.


My computer is a P4 3.2GHz, 2GB PC-3200 RAM, Asus P4C-800-E Deluxe mainboard, 3 SATA Hard Disks, ATI XT850 XT PE Video. 

I don't mind continuing to try this as long as I am learning and have some chance of success (others have succeeded so I believe its possible).  I am trying to document the steps taken so I can share them with others using this card.

Thanks in Advance for any Info or Instruction!

---

### Post by Tuf on 2006-01-16
*Bump*

---

### Post by jecos on 2006-01-16
First things first, this is linux not windows you should only have to be install **once**. You don't have to kill KDM before installing driver just restart restart after they are compiled(exception is you can modprobe but its really best to just allow it to restart everything).   

Seems like you have the info needed for your card.  Check out rage3d.com forums if you need further help with that card as there a people that have already worked through it in threads that you can just browse through.

---

### Post by Tuf on 2006-01-17
Thanks.

I have tried the Rage3D forums and the Gentoo fixes with no success.  The commands and file paths are different in Kubuntu. I am going to try Gentoo when I get a couple of days to mess with it.

---

