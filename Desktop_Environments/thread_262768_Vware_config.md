---
title: "Vware config"
date: 2006-09-22
forum: Desktop Environments
---

### Post by RGcaldas on 2006-09-22
Hi guys

I have Vmware Workstation installed, but when i did the updates to ubuntu, the vmware stop working.

so i ran /vmware/vmware-config.pl but it stops at this question:

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

I the /usr/src I only have 2 folder and both are not for the current kernel version 2.6.15-27-386)


Thanks in advance for all your help (noob here)

RG

---

### Post by RGcaldas on 2006-09-22
Its me again

just to try an place de thread in higher places ;) 

Please help, i can't find the solution for this anywhere

RG

---

### Post by amlaxaa on 2006-09-22
Hello.
I have the same problem with vmware-player. Under /usr/src i have this;
linux-headers-2.6.15-23
linux-headers-2.6.15-23-386
linux-headers-2.6.15-26
linux-headers-2.6.15-26-386

Put my running kernal is;
>uname -a
Linux lax 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686 GNU/Linux

AM

---

### Post by anaconda on 2006-09-22
You have to install new kernel headers with synaptic or apt-get..

update doesnt install new kernel headers, they must be installed manually.

---

### Post by amlaxaa on 2006-09-22
..and can you help me with that? 
I only find kernel-headers-2.4.27xxxx
But i think i need kernel-headers-2.6.15-27-386?????

Does anybody know how i can go back to running my old kernel?

AM

---

### Post by techstop on 2006-09-22
The info in this thread will help;

[http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209)

> sudo apt-get install linux-headers-`uname -r`

Or there is some more info on how to always have the kernel headers installed.

---

### Post by RGcaldas on 2006-09-22
thanks techstop it worked

it was just running your cmd and doing de vmware-config.pl again.

thanks again :D

---

### Post by techstop on 2006-09-22
Ah no worries! Lots of people are having trouble with the recent kernel update (me included). I found the fix in the original HOWTO.

---

