---
title: "Need to recover grub, need help!"
date: 2005-10-28
forum: Desktop Environments
---

### Post by Biffy on 2005-10-28
Ok, so windows crashed on me. Had to re-install. Now, it has overwritten grub and i want it back.

I've been following this guide:  

[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

First of all. I have both Windows and Linux installed on the same HDD. Linux is hda6 and windows is hda1 . My Linux partition is mounted on / . So i only have this partition. I have a swap partition too but i guess we wont be needing that one when recovering grub?

The guide asks me if i have /boot on another partition. No i dont. /boot is located on my only linux partition hda6. Also, i dont find any entries with "boot" in my fastab. Ok, so i mount everything just like the guide says:

```
mkdir /mnt/work
mount /dev/hda6 /mnt/work 
mount -o bind /dev /mnt/work/dev
mount -o bind /proc /mnt/work/proc
cp /proc/mounts /mnt/work/etc/mtab
```

This works very well. No error messages whatsoever. Now, i enter my working enviroment:

```
chroot /mnt/work/ /bin/bash 
```

This also works very well. If i type "ls" , i see the / structure of my linux partition. I see home,boot,sbin,var and so on.

It is NOW i get the problem. The guide says:

```
If you have a separate /boot/ partition, type the following line. 

mount /dev/hda3 /boot/ 

Reinstalling GRUB from this point is easy. Just enter the following command. 

/sbin/grub-install /dev/hda
```

When i type /sbin/grub-install /dev/hda i get the error message:

```
Could not find device for /boot: Not found or not a block device
```

What am i doing wrong? If i type "ls" i see a folder named boot. If i cd into the folder, all kernels,systemmaps and so on is there.

I know that i can configure it manually, but it scares me since the first solution didnt work. I am doing something wrong.

Info: I am using breezy. The liveCD im using is a hoary live CD.

Please help!

---

### Post by frodon on 2005-10-28
arnieboy posted a breezy up to date howto to restore GRUB, you should read it : [http://ubuntuforums.org/showthread.php?t=76652](http://ubuntuforums.org/showthread.php?t=76652)

It may be an easier way to do that.

---

### Post by Biffy on 2005-10-28
Actually, i solved the problem by writing GRUB to MBR manually.

---

### Post by Pathogenix on 2005-10-28
For anyone who stumbles on this, the answer is usually that your /etc/mtab is wrong.

try : cp /proc/mounts /etc/mtab

you might have to hack mtab manually in the editor of your choice.

---

