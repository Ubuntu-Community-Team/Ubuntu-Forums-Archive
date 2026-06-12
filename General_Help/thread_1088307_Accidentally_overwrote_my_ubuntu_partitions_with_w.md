---
title: "Accidentally overwrote my ubuntu partitions with windows"
date: 2009-03-05
forum: General Help
---

### Post by Castlef on 2009-03-05
Hey all.. I downloaded the windows 7 just to try it out. I should have just used a virtual machine I guess I wasn't thinking..

In the setup of windows 7 I selected it to use the first partition which was a corrupted vista install that would no longer boot. I had 2 other partitions for ubuntu (home on a separate partition)

anyways after the install of windows 7 not only did it not work (it stalls on the startup screen when it says "starting services)

but it ovverote my partition table and I assume it formatted my whole hard drive.

Is there any way to recover my data? what should I do? right now I don't even have a working operating system on the computer

---

### Post by Skripka on 2009-03-05
> **Castlef said:**
> Hey all.. I downloaded the windows 7 just to try it out. I should have just used a virtual machine I guess I wasn't thinking..

In the setup of windows 7 I selected it to use the first partition which was a corrupted vista install that would no longer boot. I had 2 other partitions for ubuntu (home on a separate partition)

anyways after the install of windows 7 not only did it not work (it stalls on the startup screen when it says "starting services)

but it ovverote my partition table and I assume it formatted my whole hard drive.

Is there any way to recover my data? what should I do? right now I don't even have a working operating system on the computer

If it overwrote the partition table (completely), and installed....odds are your data is mostly gone-a pro data recovery center might be able to get something-but I wouldn't count on it.

---

### Post by taurus on 2009-03-05
Can you boot your machine with Ubuntu LiveCD?  If you can, post the output of this command from a terminal to see if your Ubuntu partitions are still there.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
Maybe all you have to reinstall is GRUB to MBR and you will be all set again.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by BGFG on 2009-03-05
Windows seems to aggressively go after alien filesystems that it finds during install. The only way i could get XP to install recently without it inststing that it be able to write ' temporary system files' to my ext3 filesystem was to unplug both my linux drives.

It then miraculously decided that the space i had alloted was enough for install purposes. 

Taurus is your best bet. Live cd, and see what is still there if anything.

---

### Post by Castlef on 2009-03-05
Hey

I just assumed that it overwrote my partitions because when I tried the how to to restore grub it said... (after I loaded up a live ubuntu cd)

checking if "/boot/grub/stage1" exists... no
checking if "grub/stage1" exists... no

bad directory or filename

However the output of fdisk -l is that al my partitions are still there.

I have

sda1  NTFS
sda2  /
sda3  /home
swap

so four partitions

However when I restore grub like this

root (hd0,1)  # second partition of main hard drive

and then 

setup (hd0) it gives me that error I typed out above.

I can still access my files though by mounting my linux by typing

sudo mount /dev/sda2 /mnt

and then I can cd into mnt and access my filesystem

Does anyone know how to get grub back

BTW

I tried the "trick" where you load up a live cd and set the mount points but it does not let me continue without formatting... i can't trick it into installing just grub so

---

### Post by Castlef on 2009-03-06
Well I figured it out.. I had to do something before I did those grub commands to let grub discover my drives. 

I copied and pasted the commands into a text file and saved it on a usb stick so if it ever happens again I will just pop it in.. Here are the commands

> You have to mount your root partition using the livecd:

Code:



$

Code:



sudo mkdir /mnt/root



$

Code:



sudo mount -t ext3 /dev/sda6 /mnt/root



Then you have to mount the proc subsystem and udev inside /mnt/root also:

Code:



$

Code:



sudo mount -t proc none /mnt/root/proc



$

Code:



sudo mount -o bind /dev /mnt/root/dev



Doing this allows grub to discover your drives. Next you have to chroot:

Code:



$

Code:



sudo chroot /mnt/root /bin/bash



Now that you're chrooted into your drive as root everything should work.

Code:



#

Code:



sudo grub



I edited in the sudo, just to be safe. When I enter grub and not sudo grub, grub cannot find the file. I do not know if the chroot changes this because I did not try it that way. In the end I figured it was better to err on the side of caution. Tosk I hope you don't mind my editing of your reply.

grub>

Code:



find /boot/grub/stage1



It found mine on (hd0,5)

Code:



grub>

Code:



root (hd0,5)



It successfully scanned the partition and recognized the filesystem-type

Code:



grub>

Code:



setup (hd0)

---

