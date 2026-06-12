---
title: "How to using two OS??"
date: 2009-05-13
forum: General Help
---

### Post by linux_holic on 2009-05-13
How to using two OS??

because, when i install ubuntu and windows XP, there is an error...

it become error because the grub can't start....

please help me... :confused:

---

### Post by 123456789123456789123456 on 2009-05-13
a bit criptic, but here is a step by step guid to dual booting xp and Ubuntu.

step one, ensure that XP is installed.
Step 2 install Ubuntu, the partitioner should read that XP is in the first section of the hard disk, and prompt you to resize the disk, so that Ubuntu is placed at the end.  Ensure that Grub is marked to install to the MBR.  Install the OS.  It should boot normally, if GRUB installation suceeded.  The GRUB menu should read that XP is on the disk, and probably list it last in the list.  you should be able to boot either OS from this menu.

If that does not work, you need to remove the MBR listing, and Remove the Ubuntu partiton, use fixmbr from the xp recovery cd.
that should allow XP to boot, will not allow Ubuntu to boot.
You can install Ubuntu, and use ntldr, the xp boot loader to boot Ubuntu, it is a bit more difficult, but is possible.

here is the procedure for that.
after you get to the last part of Ubuntu installation, at the sumery screen, go to advanced options, tell it to install GRUB to the partition that UBUNTU is installed on or will be installed on, make sure that GRUB is not set to install on the MBR.  after installation
the computer will boot into XP
you need to edit boot.ini file in xp, create a new listing, name it Ubuntu, and use the same coding listed for the XP listing for the Ubuntu listing, but only using the information you gathered about the partion of the disk that Ubuntu is installed on.
After you restart, ntldr should ask what OS to start from, and list Ubuntu.

---

### Post by linux_holic on 2009-05-14
the grub still doesn't work....

do you have other solution????

---

### Post by KhurramM on 2009-05-14
Format the whole master disk

Plain install win xp on first primary partition

MAke partitions here if us o rquire.

Now install ubuntu on primary partitions for / and swap

It will Insha-Allah work.

OR

if u can download a SGD, it will remake the grub for u so that your current OSes are both  accessible.

**_KEY POINTS:_**
1. Install win first and then linux
2. Always install on primary partitions

Hope u can make it......

---

### Post by linux_holic on 2009-05-15
do you mean replace win with linux???

if you mean that, it must be 1 OS...

so, what should I do??

---

### Post by Bruce S on 2009-05-15
Linux_holic,

You install Windows XP, it will be located on the first partition.It must be there or it will not load up.

Then use your Linux disk , to install by following the instructions.
Read again what  KhurramM said above.

---

### Post by lilmale1 on 2009-05-15
i use vmware desktop.
virtual machine sucks
i like vmware cuz you don't have to both up one operating system at at time. you just use it from xp destop and see your way to it
its fun and much more usefull to have both on one screen

---

### Post by bacardiandwatermelon on 2009-05-15
Or you could install ubuntu using wubi from xp. This way you can play around with ubuntu and uninstall it later if you want. But you will need your pc booting into xp to run the wubi.

---

### Post by linux_holic on 2009-06-02
with your answer, i've been successfully using 2 OS...
thank you so much...:D

---

