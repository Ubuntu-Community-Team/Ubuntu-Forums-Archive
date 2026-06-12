---
title: "[SOLVED] problems installing nvidia drivers on old Dell laptop"
date: 2008-12-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by solitaire on 2008-12-29
Can anyone help me or point me in the right direction?

I'm running Ubuntu 8.10 Kernel 2.6.27-11
Graphics card "GeForce4 Go 440" mobile (Dell Inspiron 8200 laptop)
I'm trying to install the Nvidia drivers version: 96.43.09

I keep getting the following error when I install the Ubuntu version of the drivers.
     Code:
     (EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration. 
I then have to run in safe mode or use the default drivers from Ubuntu.

If i try to run the Nvidia *.run script it keeps telling me that it can not find the kernel sources (i've installed all the kernel 2.6.27-11/10/8 sources I can find!)

They were running fine until I decided to take a look at the new 2.6.28 kernel since i compiled that kernal i've not been able to get the old drivers to work properly.

If i have to do a wipe and reinstall I can use the process to resize my swap partition. 
But would like to get the graphics without the reinstall!

Any tips or am I missing something obvious?

---

### Post by 67GTA on 2008-12-29
Cards that use the 71 and 96 legacy drivers are not compatible with the xorg in Intrepid 8.10. You will have to stay with 8.04, or go without 3D support with the nv driver. Read the release notes for more info: [http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)

---

### Post by solitaire on 2008-12-29
The 96.43.09 are beta drivers from Nvidia that are compatible with the new Xorg. I've been using them fine since they were released in October.

The only thing that's changed, on my laptop, is my compile and test of the 2.6.28 Kernel using "KernelCheck". I've since removed all .28 sources and headers.

---

### Post by 67GTA on 2008-12-29
I'm confused. Are you running 8.04 or 8.10?

---

### Post by solitaire on 2008-12-29
I'm running 8.10 (Ibex)

96.43.09 release highlights:
[http://www.nvnews.net/vbulletin/showthread.php?t=122139](http://www.nvnews.net/vbulletin/showthread.php?t=122139)

---

### Post by 67GTA on 2008-12-29
I'm glad to see they are going to work for 8.10. That will make a lot of people happy. Since you have installed the newer kernel, you will have to get the source and headers for it installed, or drop back to the previous kernel and remove all traces of the 2.6.28 kernel. Each kernel has it's own headers and source.

---

### Post by solitaire on 2008-12-29
I've done all that already :(
I'm on 2.6.27-11 (what I was running before i tried 2.6.28!) and I've removed all 2.6.28 headers / source code.

This is looking to be one annoying problem :D 
Looks like it's a wipe and reinstall job :(
But i'll give it a day or 2 before i do that! (I got a post on the NVNews forum as well see what they suggest!).

---

### Post by 67GTA on 2008-12-29
How did you remove the 2.6.28 kernel? Open a terminal and run ```
locate 2.6.28
``` to see what is left. Look in /boot/grub/menu.lst to see if the 2.6.28 kernel is still listed. Once you are sure it is all gone try running ```
sudo update-initramfs
``` Then ```
sudo apt-get install build-essential linux-source linux-source-2.6.27 linux-headers-generic linux-headers-2.6.27-11 linux-headers-2.6.27-11-generic
``` Then reboot and try it again.

---

### Post by solitaire on 2008-12-29
Ah!!
Was some stray files in the Modules folders!

I've removed it all now and run "update-initramfs"
About to reboot (Think I'm down with the flu, so will leave it till the meds kick in) ;)

Thanks for your help! will let you know how i get on :D

---

### Post by solitaire on 2008-12-30
Many thanks!!

Got it fixed!

The symbolic link for the linux package was still pointing to the 2.6.28 source files.
Once that was fixed the install ran fine!! :D

Thanks again for your help.

---

