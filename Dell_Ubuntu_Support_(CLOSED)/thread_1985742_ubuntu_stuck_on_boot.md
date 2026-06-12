---
title: "ubuntu stuck on boot"
date: 2012-05-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by seansunner on 2012-05-23
im stuck in ubuntu 10 sys restore, says
GNU GRUB version 1.98=20100804-5ubuntu3.3


ubuntu, with linux 2.6.35-32- generic
same^^but with (recovery mode)next to it
Same^^ with number difference
etc.. 
and all of them show a screen and ity runs some codes and says 
killed
mount; mounting /dev on /root/dev failed; no such file or dir...
mount;mounting /sys on /root/sys failed; no such file or dir...
mount;mounting /proc on /root/proc failed; no such file or dic...
target filesystem doesnt have requested /sbin/init.
no init found. try passing init= bootarg


busybox v1.15.3 (ubuntu 1:1.15.3-1ubuntu5)built it shell (ash)

can someone help me

---

### Post by cmont899 on 2012-05-23
Is this a fresh install or did you make a change that caused this behavior?

---

### Post by seansunner on 2012-05-23
no its what my computer came with... i deleted something i wasent supost to.. iv tryed rebooting with disk but it wont work.

---

### Post by ajgreeny on 2012-05-23
So what did you delete and how?

---

### Post by seansunner on 2012-05-23
i used bleach bit and i deleted directorys on accedent. i tryed to fix it but i ended up in a mess on the recovery screen.

---

### Post by seansunner on 2012-05-23
i tryed that boot info scrip. it .i put it in and it said

 invalid system disk
replace the disk, and then press any key

---

### Post by ajgreeny on 2012-05-24
> **seansunner said:**
> i tryed that boot info scrip. it .i put it in and it said

 invalid system disk
replace the disk, and then press any key
Put it in where?

You need to boot to a live CD or USB, then download the script (link in my signature) run it as per the instructions, and copy the RESULTS.txt file back here in code tags (click the # in toolbar of reply box and paste the file [ CODE] paste here [ /CODE]

---

### Post by seansunner on 2012-05-24
i download boot repair and /or ubuntu and i put it in and it says 

missing operating system.


my computer is already fully ubuntu, so i dont know why its saying this

---

### Post by YannBuntu on 2012-05-24
Hello

> **seansunner said:**
> i used bleach bit and i deleted directorys on accedent. i tryed to fix it but i ended up in a mess on the recovery screen.

as you don't know which files where deleted, if i were you i would simply follow this to repair system files: [https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)

---

### Post by |{urse on 2012-05-24
Oh, nevermind. something else entirely. :p

---

### Post by lisati on 2012-05-24
@seansunner:
I've merged two of your threads because they look like they could be related to the same problem.

---

### Post by seansunner on 2012-05-24
it says i need to load the kernel first. what is that.



sorry .total newb question

---

### Post by |{urse on 2012-05-24
[http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-](http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-)

This will be a learning experience, 

Be sure to pay attention to the part about /dev/sdx. x should be replaced with your partition, use fdisk -l in terminal to find it.

If that doesn't work there are other things we can try.

---

### Post by seansunner on 2012-05-25
i put the live disk in and it comes on and it says to type live for the install or type memtest to test.
 i try and type sudo on that screen and it says there is not kernel.
do i need to load a kernel through the hard disk boot screen or what..

plus when i type live in the boot screen ,it starts with 

 ubuntu 11.4

in the middle of the screen , i press an f key to see the commands its running and they all say failed ,or no such file or directory.


im sorry for being a total newb, but i really need to fix my computer, its really stressing me out.please help as mush as u can, i really need it

---

### Post by |{urse on 2012-05-25
You need to select live, then open a terminal once the desktop opens. Then follow that guide. :)

---

### Post by wilee-nilee on 2012-05-25
> **seansunner said:**
> i put the live disk in and it comes on and it says to type live for the install or type memtest to test.
 i try and type sudo on that screen and it says there is not kernel.
do i need to load a kernel through the hard disk boot screen or what..

plus when i type live in the boot screen ,it starts with 

 ubuntu 11.4

in the middle of the screen , i press an f key to see the commands its running and they all say failed ,or no such file or directory.


im sorry for being a total newb, but i really need to fix my computer, its really stressing me out.please help as mush as u can, i really need it

I gave you the tools you need in your other identical thread not added to this one.

---

### Post by |{urse on 2012-05-25
Aaarg entropy.. 

Keep it on one thread. Otherwise the person(s) trying to help you only get half the story and it takes FOREVER to figure out exactly what your issue is.

---

### Post by wilee-nilee on 2012-05-25
> **|{urse said:**
> Aaarg entropy.. 

Keep it on one thread. Otherwise the person(s) trying to help you only get half the story and it takes FOREVER to figure out exactly what your issue is.

wilee-nilee at attention salutes and says "Yes Sir". :)

Posted that so all in involved could have access. 

I have stayed out of this thread, it seems this user needs to be corralled if they are to be fixed. 

This will not be fixed with a link to a how to chroot, the data needs to be gathered with the bootscript then the commands posted.

Just saying, it seems apparent at this point.

---

