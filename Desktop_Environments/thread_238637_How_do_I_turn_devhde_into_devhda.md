---
title: "How do I turn /dev/hde into /dev/hda?"
date: 2006-08-18
forum: Desktop Environments
---

### Post by glycerin on 2006-08-18
Here's the situation... up until today I've had a backup hard drive on my internal IDE. It was called /dev/hda. It is formatted to NTFS. It worked.

Today I got a new IDE card because it is faster than my internal IDE. I put the backup drive on this IDE card and booted. Now this drive is recognized as /dev/hde. I do not want this because my NTFS read-write configuration is set up to look for the drive as /dev/hda so it no longer can read/write to it.

How can I make it /dev/hda again?

---

### Post by LORD_PoLvO on 2006-08-18
Firstly its important you understand how the labeling of drives work
in linux the drives r labeled
hda
hdb
hdc
hdd
Hda is primary master
Hdb is primary Slave
hdc is secondary Master
hdd is Secondary slave

:)

now after you computer has started you need to Partition the new disk
You can do this one of two ways
1, from a commandline using the folowing commands
fdisk /dev/hdxx - to format make the partition
mkfs -t ext3 /dev/hdxx - This is to format it
2, or you can open qtparted (if you do no have qtparted run the command
apt-get install qtparted to get it

when making partitions with qtparted you generally want a maximum of 1 gig swap partition and a root linux partition / (using the rest of the space unless ur dual booting with windows)

mkdir /mnt/harddrv

now that the partitions are made you need to mount it ,
hardrives are mounted by device hda hdd hdc etc and then the partition number
witch should be 1 so change the second x to a 1
mount /dev/hdxx /mnt/harddrv - Mounting the new drive.

now all u gotta do is copy and paste the folowing commands

rsync -a --exclude="/dev" --exclude="/proc" --exclude="/sys" --exclude="/mnt/harddrv" /mnt/harddrv

mkdir /mnt/harddrv/{proc,dev,sys}

cp /dev/MAKEDEV /mnt/harddrv - this file is needed for making device nodes

cd /mnt/harddrv/dev

./MAKEDEV generic-i386

Done now reboot open you bios and set it to boot from you new hardrive



this should work it did for me :)

---

### Post by aysiu on 2006-08-18
I think the letter assignments are based on the order in which things are plugged in.

Unless you unplug all your devices and then replug them in so that your new drive is first, it won't be /dev/hda.

Why not change your NTFS read-write configuration instead?

---

### Post by ciscosurfer on 2006-08-18
I agree with aysiu...it's a whole lot easier to just modify your NTFS configuration (via your fstab).  

Just modify the line that reads /dev/hda  and change it to /dev/hde instead -- that should do it.

:-D

---

### Post by LORD_PoLvO on 2006-08-18
yeah i didnt think of that im into doing things the hard way though :):-k

---

### Post by glycerin on 2006-08-20
> **LORD_PoLvO said:**
> Firstly its important you understand how the labeling of drives work
Hda is primary master
Hdb is primary Slave
hdc is secondary Master
hdd is Secondary slave

Thanks for this information. I didn't know that so now it makes sense why it is called hde.

> **ciscosurfer said:**
> I agree with aysiu...it's a whole lot easier to just modify your NTFS configuration (via your fstab).  

Just modify the line that reads /dev/hda  and change it to /dev/hde instead -- that should do it.

I figured changing the config would take a lot more work but it didn't. This was a quick and easy fix, thanks!

---

