---
title: "Ubuntu and Vista to share same home drive"
date: 2009-04-23
forum: General Help
---

### Post by optimistique1 on 2009-04-23
Hi All

I am dual booting with WIN Vista and Ubuntu 9.04 and I am sure I have read somewhere that there is a way for both OS's to share the same home drive.
Has anyone any idea how to go about doing this?
Many thanks:)
Garry

---

### Post by Monotoko on 2009-04-23
Well, you can partition the hard-drive, and install one OS to one partition and the other to the other partition.

Or you can stick the disk in while Windows is on, and it will come up with an option for installing inside windows, however, you are definatly best duel-booting.

---

### Post by ubu-for on 2009-04-23
Try this Windows program to read/write ext2/3 Linux partitions.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by prem1er on 2009-04-23
I also think there is an easier way. Someone can help me out with this, but if you make the /home partition NTFS you will be able to mount that partition in Ubuntu and be able to read/write from both Windows and Ubuntu.

---

### Post by ubu-for on 2009-04-23
> **prem1er said:**
> Someone can help me out with this, but if you make the /home partition NTFS ...

I wouldn't recommend that.

---

### Post by leandromartinez98 on 2009-04-23
I don't think you will be able to use "the same home" directory
for both, since there are many configuration files that are stored
in both main home/user directories that you don't create yourself.

But probably you just want to work on your windows files from
Ubuntu (the contrary is impossible, since windows cannot mount
ext3 partitions). If this is the case, you can mount the Windows
partition using the Home->Places, the windows partition is visible
there and can be mounted, and the files can be used. You can mount
that partition automatically on boot by adding a line to your
/etc/fstab file. 

If you want that your home directory appears than as a sub-directory
of your home in Ubuntu, you may add a simbolic link to it, using:

ln -s /media/disk/Users/username ~/WindowsHome

(probably /media/disk is where your Windows partition
is mounted and /Users/username is your home windows directory there).

This will create a link to your home windows folder on your home Ubuntu folder, such that it will look like a subdirectory of it.

---

