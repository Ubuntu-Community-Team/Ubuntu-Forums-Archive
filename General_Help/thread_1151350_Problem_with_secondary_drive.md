---
title: "Problem with secondary drive"
date: 2009-05-06
forum: General Help
---

### Post by AllRadioisDead on 2009-05-06
I just did a fresh install from windows xp, and I have a secondary drive with some important data on it, but whenever I try and access it, I get an error. I believe it's formated with NTFS and after hitting "Ok" twice I get an error that the directory doesn't exist.

---

### Post by mb_webguy on 2009-05-06
Well, you could try mounting it from the terminal.

Open the terminal and enter the command "sudo fdisk -l" (that's a lower-case L, not a 1).  This will show you all of your drives and partitions, and the associated device files (the /dev/xxxn part).  Make a note of the device file for the partition you're trying to access.

Now create a directory to use as a mount point, using the command "sudo mkdir /mnt/*something*", where *something* is anything you want to name it.  Mount the partition using the command "sudo mount /dev/*xxxn* /mnt/*something*", where *xxxn* is the device file for the partition.

---

### Post by AllRadioisDead on 2009-05-06
By the looks of it, it's already mounted isn't it? I'm referring to the 500gb drive on the location list.

---

### Post by colau on 2009-05-06
> **ihermit said:**
> I just did a fresh install from windows xp, and I have a secondary drive with some important data on it, but whenever I try and access it, I get an error. I believe it's formated with NTFS and after hitting "Ok" twice I get an error that the directory doesn't exist.
This may help.
[http://ubuntuguide.org/wiki/Dapper#Windows](http://ubuntuguide.org/wiki/Dapper#Windows)

---

### Post by AllRadioisDead on 2009-05-06
> **mb_webguy said:**
> Well, you could try mounting it from the terminal.

Open the terminal and enter the command "sudo fdisk -l" (that's a lower-case L, not a 1).  This will show you all of your drives and partitions, and the associated device files (the /dev/xxxn part).  Make a note of the device file for the partition you're trying to access.

Now create a directory to use as a mount point, using the command "sudo mkdir /mnt/*something*", where *something* is anything you want to name it.  Mount the partition using the command "sudo mount /dev/*xxxn* /mnt/*something*", where *xxxn* is the device file for the partition.
Worked, sorry about the above post.

---

