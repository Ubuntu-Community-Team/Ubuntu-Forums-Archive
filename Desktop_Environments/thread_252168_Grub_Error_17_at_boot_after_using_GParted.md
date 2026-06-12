---
title: "Grub Error 17 at boot after using GParted"
date: 2006-09-06
forum: Desktop Environments
---

### Post by Exakun on 2006-09-06
I had installed Ubuntu on my laptop, and I was planning on installing Windows XP to dual-boot, but I discovered VMWare Server and had changed my mind to using that to run Windows instead. Because I had originally planned to install Windows XP onto a disk partition, I made an NTFS volume with which I could do so, but I decided to reallocate that space for use in the Windows XP VM. I had to use the Dapper Drake Live CD to use GParted on my current partitions (only one HDD) so I could reallocate that space, but now I am getting GRUB Error 17 at boot.

Originally, my HDD Partitions were:

(NTFS for Windows XP) (EXT3 for Ubuntu install) (Linux-swap) (EXT3 for /home)
Please note that the NTFS portion had not been used, and that none of these partitions were Extended- or Logical-type.

What I did was delete the NTFS Partition, copy my Ubuntu install partition into the empty space, delete the old install partition, copy my linux-swap partition into the space and delete the old swap, then copy my /home directory into the allocated space and extend it to the end of the disk. My new configuration is now: (EXT3 Ubuntu Install) (linux-swap) (EXT3 /home).

Because of the magnitude of the operation, I left it running overnight (It was going to take an hour and it was already uncomfortably close to 3:00am). I attempted to boot this morning to find that I am unable to load the GRUB boot manager. I even attempted to load the LiveCD using "boot: recovery" but it still yields the same result: 

[I]
Booting from local disk...
GRUB Loading stage1.5

GRUB Loading, Please Wait...
Error 17
_ [/I]

Is there a way I can fix this problem, or was moving my partitions around a bad thing? I would prefer not to have to reinstall Ubuntu (not to mention all the software I've installed since), but if there is no solution I guess I'd have to.

Any help with this issue would be most appreciated. Thank you in advance for your time.

---

### Post by bulldog on 2006-09-06
The reason you get an error is that your partitions are wrong in your grub,menu.lst en fstab
You have to find out what they are en alter your menu.lst en fstab manually.
If I understand your post well,I think that your boot should be hdd0,0.
But do the following to find out what your boot partition is callled.
Then use your disk tool to see what the others are numbered and change the values in menu.lst en fstab.

This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

Code:

find /boot/grub/stage1

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

Code:

root (hd?,?)

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

Code:

setup (hd0)


Finally exit the grub shell
Code:

quit

Don't forget to alter your menu.lst AND your fstab!!!!

---

