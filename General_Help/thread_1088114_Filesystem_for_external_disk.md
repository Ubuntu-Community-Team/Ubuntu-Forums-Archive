---
title: "Filesystem for external disk"
date: 2009-03-05
forum: General Help
---

### Post by jaminux on 2009-03-05
Hi all,

Earlier I was backing up a 5.4 GB tar archive on my external hard disk formatted as fat32. At 4.0 GB the transfer suddenly terminated. Thinking it was a random bug I tried doing it again. Same result.

After I did a little googling I came up with a wikipedia page with the information on the maximum file size of filesystems... the maximum on fat32 is of course 4.0 GB (duh!).

Anyway, my question is:

What is the best filesystem to format my external hard disk to if I want to store large files and maintain Windows compatibility? 

I am aware there is NTFS but I am always wary of Windows junk that does not have full Linux support. Are there any alternative filesystems?

---

### Post by taurus on 2009-03-05
NTFS is your best bet but if you want to format it to ext2/ext3, then you need to install fs-driver in windows so windows can read that harddrive.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by jaminux on 2009-03-05
I think it is got to be NTFS (:(). I won't necessarily be able to install drivers on the Windows machines I want to use the external hard disk with. 

Anyway, thanks for the links on ext drivers. I will definitely install those on my Windows machine.

---

### Post by taurus on 2009-03-05
Just remember to use the _safely remove hardware_ option in windows to unmount the drive before you unplug it.

---

### Post by Vince4Amy on 2009-03-05
Your most reliable option is NTFS. Don't worry NTFS is supported through ntfs-3g and works great out of the box in most distros.

---

### Post by jaminux on 2009-03-05
Thanks everyone...

Now I just have to transfer 36 GB off the drive then back on again. ;)

---

