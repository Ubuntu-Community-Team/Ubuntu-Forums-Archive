---
title: "Windows drive won't boot, won't mount in linux (USB)"
date: 2009-02-11
forum: General Help
---

### Post by Wolfin on 2009-02-11
So I have this hard drive, used to be in my sister's laptop, and I'm trying to get her files off of it. It got a BSOD during the Windows boot screen, so I figure one or more of the boot files is corrupted.

Naturally I threw it in a USB external enclosure and booted into Ubuntu.. 
But it wouldn't mount, either, because it had a "Unclean Shutdown" flag. So I can't boot it, nor find its label to force mount it (if I knew how).

Can anyone help?

Trying to access the drive on a Windows machine locks up explorer. "Safely Removing" it doesn't work, no response.

Trying to access the drive with gparted locks up gparted.

It's an 80GB drive, and I don't have the space to do a bitwise copy without wiping either my Ubuntu partition or my Windows 7 partition.

---

### Post by bodhi.zazen on 2009-02-11
sounds like a hardware problem.

What happens when you try to mount it ?

List your partitions with 

```
sudo fdisk -l
```

Then

```
sudo mount /dev/sdb1 /mnt
```

Assuming the partition in question is /dev/sdb1

You can try forcing the mount and / or data recovery such as testdisk / photorec as well.

---

### Post by trikster_x on 2009-02-11
I had a similar problem with a HDD of my own.  My comp crashed in the middle of an XP session and would not allow me to boot into it anymore, saying there was a memory error.  It turns out that the if windows crashes, there is a small chance that XP will be stuck in an online mode of sorts and is awaiting a safe shutdown, which can only be done by booting windows (which can't be done).  I don't remember the exact command, but I ended up having to force the drive to mount in Ubuntu to save my important files.  I was actually given the command to run in the error details part of the "failed to mount" window that popped up.  But I had linux on the same HDD in a seperate partition, so this may have been of no help to you.  Maybe try using a liveCD on the HDD with the problem, to force a mount of the partition.  Just remember that a forced mount can have bad consequences, such as data loss.  Sorry I don't have the actual command, but at least you have a starting point.

---

### Post by JK3mp on 2009-02-11
As stated could be a hardware problem...is it reading that its there at all. If not could be ruined HDD...mishandled..etc.

---

### Post by bodhi.zazen on 2009-02-11
sudo mount -o force /dev/sdb1 /mnt 

:twisted:

---

### Post by Wolfin on 2009-02-11
Okay, I understand the force mount - but when I try it, I get:

mount: can't find /dev/sdb1/mnt in /etc/fstab or /etc/mtab

fstab doesn't exist, so should I try and add the device to mtab?

---

### Post by trikster_x on 2009-02-11
'sudo mount -o force /dev/sdb1 /mnt' should work if it is typed correctly and your drive has the same path.  There should be a space between the /dev/sdb1 path and /mnt destination.  Can linux see the drive at all when you look at the computer window?

---

### Post by Wolfin on 2009-02-11
> **trikster_x said:**
> 'sudo mount -o force /dev/sdb1 /mnt' should work if it is typed correctly and your drive has the same path.  There should be a space between the /dev/sdb1 path and /mnt destination.  Can linux see the drive at all when you look at the computer window?


Right, right - missed the space before /mnt 

Works!

Thanks everyone, you were a big help.

---

