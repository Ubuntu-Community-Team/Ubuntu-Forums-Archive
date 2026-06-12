---
title: "Option to Choose OS"
date: 2009-01-03
forum: General Help
---

### Post by generic_idea_machine on 2009-01-03
I just installed another debian based distro on an altogether separate IDE drive. (Ubuntu is running as the primary OS on a SATA drive). 

The system directly boots to Ubuntu. I'd like to have the option to  choose the which OS to boot into. Can't see anything under the system settings.

Settings from BIOS:
- IDE Drive : Identified as Primary Master IDE (This is where the other distro was installed)
- Two Other SATA drives. (Ubuntu (mbr) is on one of the Sata drives)

Anyone run into the same issue? :confused:

---

### Post by Sin@Sin-Sacrifice on 2009-01-03
Do you have grub? I don't know how it works with separate hard drives but that's the first thing I can think of. Otherwise you can hit a key upon reboot to enter the boot options and select the other HDD. Mine's esc but some people have F8 and others.

---

### Post by generic_idea_machine on 2009-01-03
> **Sin@Sin-Sacrifice said:**
> Do you have grub? I don't know how it works with separate hard drives but that's the first thing I can think of. Otherwise you can hit a key upon reboot to enter the boot options and select the other HDD. Mine's esc but some people have F8 and others.

I think so:

```
guyfawkes@robocop:/boot/grub$ 
guyfawkes@robocop:/boot/grub$ ls -ltr
total 204
-rw-r--r-- 1 root root   9276 2008-07-22 22:30 xfs_stage1_5
-rw-r--r-- 1 root root    512 2008-07-22 22:30 stage1
-rw-r--r-- 1 root root   9632 2008-07-22 22:30 reiserfs_stage1_5
-rw-r--r-- 1 root root   7324 2008-07-22 22:30 minix_stage1_5
-rw-r--r-- 1 root root   8608 2008-07-22 22:30 jfs_stage1_5
-rw-r--r-- 1 root root   7904 2008-07-22 22:30 fat_stage1_5
-rw-r--r-- 1 root root   8056 2008-07-22 22:30 e2fs_stage1_5
-rw-r--r-- 1 root root     30 2008-07-22 22:30 device.map
-rw-r--r-- 1 root root    197 2008-07-22 22:30 default
-rw-r--r-- 1 root root 108356 2008-07-22 22:30 stage2
-rw-r--r-- 1 root root     16 2008-07-22 22:30 installed-version
-rw-r--r-- 1 root root   4703 2009-01-02 21:35 menu.lst~
**-rw-r--r-- 1 root root   5135 2009-01-02 21:35 menu.lst**

```

Do I have to edit the menu.lst to include the other OS?

thanks for the quick reply!

---

### Post by generic_idea_machine on 2009-01-03
Did a bit more research into editing grub last night. 

Sounds like a good 2,3 hour project for me (As I anticipate I'd be running into more then a couple of problems updating grub)

F8 it is... for now

---

### Post by linux_tech on 2009-01-03
Open Terminal:Applications -> Accessories -> Terminal
Check what OS is on which partition-
```
   df -h
```

In menu.lst you have to add the OS entry, for example if you want to add XP-
```
title XP
root (hd0,0)  <--- but you will need to edit this option
makeactive
chainloader +1
```

To do this navigate to /boot/grub and enter the following:
```
sudo gedit menu.lst
```

---

### Post by drs305 on 2009-01-03
> **generic_idea_machine said:**
> Did a bit more research into editing grub last night. 

Sounds like a good 2,3 hour project for me (As I anticipate I'd be running into more then a couple of problems updating grub)

F8 it is... for now

You can edit grub (assuming you have it) with a gui app called StartUp-Manager which will allow you to set the menu display timeout, which OS to start with, how many updated kernels to display, and lots of other tweaks. ***If*** StartUp-Manager (SUM) can see your other OS's, it is the easiest and safest way for someone who is unwilling or uncomfortable with editing menu.lst manually. It won't *add* other OS's but it will help select the options once the systems are listed in menu.lst

Here is the link to a tutorial which describes how to install and use StartUp-Manager:
[StartUp-Manager and Editing menu.lst - Intro]("http://ubuntuforums.org/showthread.php?t=818177")

---

