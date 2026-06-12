---
title: "A strange problem! ubuntu hangs on my system"
date: 2010-10-28
forum: Desktop Environments
---

### Post by farzad_a on 2010-10-28
Hi all my friends.
I'm glad to be a new member of this forum where I can share ideas with friends all over the world.
I'm a programmer, mostly MATLAB for relatively light and Fortran for  heavy calculations. I switched from windows to ubuntu because of its  greater speed. My programs in Fortran run about 2.5X faster on ubuntu!  Recently, I got 2 new PCs in the research lab. Both are same in  hardware:
AMD Phenom II X6 1090T processor
BIOSTAR TA890GXE motherboard (onboard ATI VGA)
500 GB HDD

Installed on the systems are Windows 7 ultimate and ubuntu 10.04 LTS  (both 64bit versions). Windows 7 works very well with ABSOLUTELY no  problem. It has good speed and stability. All softwares work fine. On  ubuntu, however, I have some strange problems which I cant find the  cause. The system hangs in ubuntu very often. These are the usual events  after which the system hangs:

[LIST]
[*]when the system goes to screensaver, on resume a blank screen is  displayed with the mouse cursor. All I can do is moving mouse, no  keyboard shortcut works. The only way to get out is by pressing the power or reset button on case.
[*]after a hangup, pressing the reset button reboots my system in a  situation where no boot option is displayed!!! (A problem with grub, I  think)
[*]However, pressing the power button to power off and again to power on, restores the grub menu, which appears to be fine
[*]Sometimes accessing the NTFS partitions on my disk (windows  partitions) may cause a crash and I receive an error like this  "Read-Only File System" after which nothing works. after reboot an automatic disk checkup resolves the problem.
[/LIST]
 I also installed fedora 13 desktop (64 bit) and I got EXACTLY the SAME  problems. Is it related to the hardware on systems? In that case I have  to forget Linux?!!!!! :sad: Or it may be related to Gnome environment (since both ubuntu and fedora use it)? I searched the forum and found similar problems with screensaver on ATI card.
The problems are not permanent, sometimes they appear, more times not!
I'm curious to know if anyone has faced similar problems or knows the solution. Excuse me for this long post.

---

### Post by prasadpkamath on 2010-10-28
yeah, i had these problems too. turned out that the HDD was ailing. it crashed eventually. i have now got a new HDD and everything works fine. perform a disk check and in case of any errors, if you have a seagate HDD, i would recommend you to use seatools to check your drive.

---

### Post by farzad_a on 2010-10-28
Thank you. So, you think the problem is with hard disk... 
But in Windows 7 everything is fine, with absolutely no problem.
Nevertheless, I will check it and let you know if it worked
Thank you again

---

### Post by rsk02 on 2010-10-28
From what I can see, there is no reason to conclude that you have a faulty HDD. I suggest you disable compiz and see if the problem persists. Your power switch may be programmed to suspend on click (4 secs to poweroff). That would explain the grub menu issue. What application is accessing the ntfs drive when you see the "crash"? How is the ntfs partition mounted in fstab?

---

### Post by farzad_a on 2010-10-28
> **rsk02 said:**
> From what I can see, there is no reason to conclude that you have a faulty HDD. I suggest you disable compiz and see if the problem persists. Your power switch may be programmed to suspend on click (4 secs to poweroff). That would explain the grub menu issue. What application is accessing the ntfs drive when you see the "crash"? How is the ntfs partition mounted in fstab?

Thank you rsk02. As you said, the HDD has no fault.
When ubuntu starts, I see all partitions mounted automatically. I dont know how they mount, but surely default settings are not changed.
About the grub menu, you think that there is no problem to concern and its behavior is natural?
I'm really a beginner with Linux and ubuntu, I think compiz is related to visual effects, but dont know even if it is installed and how it can be disabled. Ubuntu was installed by the standard CD and updated automatically on first use with no problem. Would you please explain how I can disable compiz?
Thanks again

---

### Post by theozzlives on 2010-10-28
> **farzad_a said:**
> Thank you rsk02. As you said, the HDD has no fault.
When ubuntu starts, I see all partitions mounted automatically. I dont know how they mount, but surely default settings are not changed.
About the grub menu, you think that there is no problem to concern and its behavior is natural?
I'm really a beginner with Linux and ubuntu, I think compiz is related to visual effects, but dont know even if it is installed and how it can be disabled. Ubuntu was installed by the standard CD and updated automatically on first use with no problem. Would you please explain how I can disable compiz?
Thanks again

In most circumstances, you right-click on your desktop > change desktop background > go to visual effects tab > choose none. Also go to terminal and post the output of:
```
cat /etc/fstab
```

---

### Post by farzad_a on 2010-10-30
This is the output of the command "cat /etc/fstab" typed in the terminal:

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=b479f15c-2cad-4a37-8250-f7cf56345a8b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=15fabe4e-2ff7-4442-956c-dcb229a057d1 none            swap    sw              0       0

```

I dont understand this :( any idea?

---

### Post by farzad_a on 2010-10-30
> **theozzlives said:**
> In most circumstances, you right-click on your desktop > change desktop background > go to visual effects tab > choose none. Also go to terminal and post the output of:
```
cat /etc/fstab
```
Thank you theozzlives. posted above is the output of command. The visual effects are disabled as you guided. The problem still remains!

Is there any reason to think Windows 7 could not be matched with ubuntu 10.04? I think these OS try to take control of the system (specially Win 7) on boot options, etc. Therefore the whole system will not run correctly. So, read this:
Today, after disabling visual effects on one of my systems, ubuntu runs stable and with no problem. But Win 7 will reboot the system after only about 30 secs from startup, when a crash occurs!
I checked the mainboard's manufacturer website and on the OS tab, found only Windows XP, Vista, 7 ...
No UNIX or Linux OS was mentioned for the mainboard.
Could it be the incompatibility of hardware with Linux?

So, I'm going crazy..... unfortunately, if the problem persists, I have to forget ubuntu...

---

### Post by farzad_a on 2010-10-31
The problem was with the physical memory (RAM). 2 x 2GB was installed on the mainboard. after excessive physical memory test, I found that one of them had problems. replacing the RAM fixed all my problems. Thank you all my friends and sorry for taking your time.

---

