---
title: "Mounting Windows Files?"
date: 2009-05-27
forum: General Help
---

### Post by megamouthbolt on 2009-05-27
I recently have been interested in mounting windows files through ubuntu. However, the problem is that all the guides I have read so far involve ubuntu installed on a **partition**.

I used Wubi, however, and I want to know how I can access my windows drive (C drive) through Ubuntu. 

When I run:

 ```
root@ubuntu:~# fdisk -l
```

I get: 

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbbc58b91

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1339    10755486    7  HPFS/NTFS
/dev/sda2   *        1340       35418   273735560    7  HPFS/NTFS


```



instead of something similar to this:
(note I got this from this guide) [http://www.technixupdate.com/mount-ntfs-fat32-windows-drive-in-ubuntu/](http://www.technixupdate.com/mount-ntfs-fat32-windows-drive-in-ubuntu/)

[[IMG]http://www.technixupdate.com/wp-content/uploads/2008/12/terminal-windows-drive-listing.jpg[/IMG]]("http://www.technixupdate.com/wp-content/uploads/2008/12/terminal-windows-drive-listing.jpg")

---

### Post by Locutus_of_Borg on 2009-05-27
what does 'mount /dev/sda2 /mnt' do?

never used wubi, but it looks like that should still work?

---

### Post by megamouthbolt on 2009-05-27
It brings up the "Computer" mount in Places, but when I open it, it does not give me access to the windows files. 

To me, it seems that I have to install Ubuntu on a partition to access my files.

Does anyone have a suggestion?

Note: I read that LVMP [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html) can convert Wubi to partition, but it is not compatible with Jaunty.

---

### Post by Locutus_of_Borg on 2009-05-27
that is very odd behavior..

what is the output of:```
sudo -i
mount /dev/sda2 /mnt
ls -R /mnt
```

---

### Post by bbboB on 2009-05-28
I'm running Jaunty using Wubi and my host system is Vista.  
Not sure what Windows system you are using, but I suspect that using Wubi is the same across the board.

Go to Place-->Computer and then double click the File System icon.
In this window you will see a folder called "Host."
Opening this folder will give you access to the Windows system and allow you access to all the shared folders (or maybe others...I've never tried it) on your host system.

Someone else posted this solution on the boards, but I can't find the original post, so I can't give credit where credit is due.

---

### Post by megamouthbolt on 2009-05-29
Thank you both so much!

sudo -i
mount /dev/sda2 /mnt
ls -R /mnt
Gave me what is seemingly a list of all the files found in the "Host" folder, as bbboB instructed me to enter.

Thanks!

---

