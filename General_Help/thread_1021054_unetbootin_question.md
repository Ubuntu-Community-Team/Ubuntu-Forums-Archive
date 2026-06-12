---
title: "unetbootin question"
date: 2008-12-24
forum: General Help
---

### Post by Seks on 2008-12-24
I just used unetbootin to make an intrepid live USB thumbdrive, the second time (selecting /dev/sdb1) it worked fine. 

The first time though I used /dev/sdb, which confused it and )from the looks of things) it installed to my hard drive through a folder in /media/ (which is normally used for mounting). I noticed a step in the installation was "installing bootloader", and since it was doing stuff to my harddrive, I'm worried it could have messed up my grub (or any number or things). Menu.lst is intact and my ntfs drive still has the boot flag, but I have little knowledge of how the master boot record works.

So what does "installing bootloader" do, and will my computer boot up normally next time? How do I view my MBR?

---

### Post by ju2wheels on 2008-12-26
No worries, you did your system no harm. 

The /media/ folder is used for auto mounting added physical media such as usb hard drives or pen drives and the cdrom. /dev/sdb therefore refers to your physical usb drive where /dev/sdb1 refers to the first partition on that usb drive. /dev/sdb is where you would want the boot loader placed anyway, so you did your system no harm. 

The bootloader is the application which loads the Linux kernel and begins the OS boot up process.

---

