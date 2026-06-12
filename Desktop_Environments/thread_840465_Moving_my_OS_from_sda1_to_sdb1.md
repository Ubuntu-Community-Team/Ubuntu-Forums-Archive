---
title: "Moving my OS from sda1 to sdb1"
date: 2008-06-25
forum: Desktop Environments
---

### Post by nate305 on 2008-06-25
Hello all, 

I've got 2 HD's Ubuntu installed on a 160GB and a newly added 60GB thats empty.  What i'd like to do is move the OS to the 60GB and use the 160GB drive for my data. I'm assuming i can copy OS files to 60GB drive, move home folder over and change settings in boot loader but i haven't got a tremendous amount of linux experience. My questions are...
a. will this work
b. am i missing anything
c. how do i alter boot loader

OS is on /dev/sda1, i'd like it on /dev/sdb1

thnx in adv..

---

### Post by logos34 on 2008-06-25
If you mean /home is on a separate partition, it should be even easier.  You'd just copy over / to 60 gb drive.

post

sudo fdisk -l

You could use [Gparted]("http://gparted.sourceforge.net/larry/move/move.htm") or [dd command]("http://www.brunolinux.com/02-The_Terminal/The_dd_command.html")

---

### Post by nate305 on 2008-06-25
as it stands everything is on 1 partition on the 160G disk, but i want to use the 160 for all data and the 60 for OS, i could just copy /home to 60 but i'm shooting for the opposite as the 160 will give me more room for data and the 60 should be way more than enough for OS files.

---

### Post by logos34 on 2008-06-25
here's how I'd do it:

-boot from the live cd and copy over entire / partition.

-make a new swap on the 60 gb drive or just leave it where it is

-transfer /home folder to a separate partition on the 160 gb using[ this guide]("http://www.psychocats.net/ubuntu/separatehome")

-edit /etc/fstab and /boot/grub/menu.lst

-[reinstall grub ]("http://ubuntuforums.org/showthread.php?t=224351")to the mbr of the 60 gb drive

---

