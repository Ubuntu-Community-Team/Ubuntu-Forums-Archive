---
title: "Stops during boot and install"
date: 2010-05-11
forum: Desktop Environments
---

### Post by wweeks on 2010-05-11
My computer (Toshiba Satellite L500) stops during the middle of boot. It is a 64 bit system. I've tried both the 64x and the 86x versions of Ubuntu 10.04 LTS.  Here is the last thing that loads with the 64x version when booted in normal mode (with both LiveDVD and Wubi install).
> [0.873922] [<ffffffff810141e0>] ? child_rip+0x0/x20Here is what I get in safe graphics mode.
> [0.893197] [<ffffffff810141e0>] ? child_rip+0x0/x20Does anyone know what the problem is?
P.S. I've tried Ubuntu 9.10 Desktop and Netbook Remix too and neither of those work.

---

### Post by wweeks on 2010-05-14
Could anyone help me?

---

### Post by mErchamion on 2010-05-15
I have almost the same problem ( messages are quite different). Let me give you the details.

I have recently acquired a Toshiba Satellite L500-ST5507:
Intel I5 430 Processor, DDR3 memory, Intel Integrated Graphics, Intel 5  series 4 port SATA AHCI Controller, Realtek RTL 8191SE Wireless LAN,  Intel 5 series/3400 series Chipset family USB Enhanced Host controller  3B34.
In this laptop, I have been able to boot ubuntu 9.01, though i couldnt  get the wireless to work (among other things). 

Now, I wanted to try Ubuntu 10.04, but I find that I can not even boot  the computer. When I boot from the live cd, I can see the menu screen,  but when I choose the "try without installing" option, all I get is a  screen full of weird messages, the last two of them are:

[0.600438][<c0104087>] kernel_thread_helper + 0x7/0x10
[0.600375][<c07a3308>] kernel_init + 0x0/0xbf
I tryed wubi installation, but the same screen comes up when rebooting. 

after sugestios from Linux Forums guys, I checked for bios settings for SATA controllers, but no change on this settings worked. I also run md5 sum on the downloaded iso image and I got a result included in the Ubuntu Hashes page. 

I was successful in installing Ubuntu 10.04 in a Virtual Box machine with this live CD.

I will be very thankful if anybody can explain me what the problem is and if there is a way to solve this issue. Waiting for your response!

---

### Post by sriramoman on 2010-09-09
Same problem with Toshiba L500, i3 processor, ATI graphics. 
Actually, at installation time, I selected **noapic, acpi=off** and all the settings under F6 option except *"Free software only"*.
This machine is without any other OS except the (k)ubuntu.
After rebooting the installed system, the installed system gives the same *child_rip* error and hangs during boot. I tried editing **/etc/default/grub** using the rescue cd and added the **noapic, acpi=off** and ran a grub-install on the hard disk. But it does not fix the problem.
If anyone could throw light on how to disable acpi persistently and also include a timeout in Grub2 for ubuntu-only machines, it would be appreciated!

---

### Post by mErchamion on 2010-11-28
Hi there! I worked out a solution for the toshiba acpi incongruence. I report this solution in this thread:
[http://ubuntuforums.org/showthread.php?t=1486007&highlight=toshiba](http://ubuntuforums.org/showthread.php?t=1486007&highlight=toshiba)

but you can also follow the instructions for patching the linux source here:
[http://homeport.org/~bcordes/satellite-l500-install.html]("http://homeport.org/%7Ebcordes/satellite-l500-install.html")

Compilation instructions are very clear here:
[https://help.ubuntu.com/community/Kernel/Compile#Alternate%20Build%20Method:%20The%20Old-Fashioned%20Debian%20Way](https://help.ubuntu.com/community/Kernel/Compile#Alternate%20Build%20Method:%20The%20Old-Fashioned%20Debian%20Way)

I have been successful in applying this for maverik 2.6.35 kernel, and my laptop is working flawlessly right now.

See you all!

---

### Post by wweeks on 2011-04-11
This problem has been resolved in Ubuntu 10.04.

---

### Post by sriramoman on 2011-10-16
Things are perfect from Natty Narwhal onwards in Toshiba L500.

---

