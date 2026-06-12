---
title: "NTFS Partition problem!"
date: 2009-04-18
forum: General Help
---

### Post by gaalaaant on 2009-04-18
So I have a Dual boot Vista 32 and Intrepid Toshiba Laptop.  I have 4 partitions, devsda1 being Vista, 2 being Intrepid, 3 being my "Media Partition" like where I store all my docs and movies, and 4 being a swap space.  Now My problem is that I recently reformatted devsda3 from fat32 to NTFS because I couldn't torrent files larger than 4gb in fat32.  I reconstructed the system trees EXACTLY (which took forever b/c I didn't have a external hard drive, so I had to copy it all onto SL DVD's).  Now when I boot into Ubuntu, I can't access my partition, which used to be on /media/mystuff/, and it shows up as a 115 gb partition like it did before when I accidently didn't mount it when installing ubuntu.

---

### Post by tofiluk on 2009-04-18
> **gaalaaant said:**
> So I have a Dual boot Vista 32 and Intrepid Toshiba Laptop.  I have 4 partitions, devsda1 being Vista, 2 being Intrepid, 3 being my "Media Partition" like where I store all my docs and movies, and 4 being a swap space.  Now My problem is that I recently reformatted devsda3 from fat32 to NTFS because I couldn't torrent files larger than 4gb in fat32.  I reconstructed the system trees EXACTLY (which took forever b/c I didn't have a external hard drive, so I had to copy it all onto SL DVD's).  Now when I boot into Ubuntu, I can't access my partition, which used to be on /media/mystuff/, and it shows up as a 115 gb partition like it did before when I accidently didn't mount it when installing ubuntu.

have you tried using gparted?

---

### Post by justin_guerin on 2009-04-18
> **gaalaaant said:**
> So I have a Dual boot Vista 32 and Intrepid Toshiba Laptop.  I have 4 partitions, devsda1 being Vista, 2 being Intrepid, 3 being my "Media Partition" like where I store all my docs and movies, and 4 being a swap space.  Now My problem is that I recently reformatted devsda3 from fat32 to NTFS because I couldn't torrent files larger than 4gb in fat32.  I reconstructed the system trees EXACTLY (which took forever b/c I didn't have a external hard drive, so I had to copy it all onto SL DVD's).  Now when I boot into Ubuntu, I can't access my partition, which used to be on /media/mystuff/, and it shows up as a 115 gb partition like it did before when I accidently didn't mount it when installing ubuntu.
By default, Ubuntu mounts partitions using block IDs.  Since you reformatted /dev/sda3, it'll have a new block ID.  

To find the new block ID, run the command "blkid -L" (without the quotes).  Grab the block ID from the output, and change the mount options in /etc/fstab.

If the block ID is blank, then change the format of the mount in /etc/fstab to be /dev/sda3 (or whatever is appropriate for that partition).

Don't forget to change the mount type.  Before, it was vfat, but now it'll need to be ntfs.

---

### Post by gaalaaant on 2009-04-19
WOW, you know what's weird, I read the responses in Vista, emailed the link to myself, read it here, went to try your advice.  And when I open nautilus BAM my 115 gb partition is MOUNTED.  It works great, but for some reason it tells me that the partition is a picture cd, is that bad?

---

### Post by justin_guerin on 2009-04-19
If I had to guess, it's related to bug 258936:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/258936](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/258936)

I would guess you're fine.

---

### Post by gaalaaant on 2009-04-19
Thanks Guys!  Jeez I wish every forum was like this.

---

