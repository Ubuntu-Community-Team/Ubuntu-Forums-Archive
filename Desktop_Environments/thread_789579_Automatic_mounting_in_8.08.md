---
title: "Automatic mounting in 8.08"
date: 2008-05-10
forum: Desktop Environments
---

### Post by Joakim Stokland on 2008-05-10
Hi!
I recently installed Hardy, and after I did, the two "non-linux-partitions" (Windows and one for files that Windows and Linux share, such as music and pictures) don't mount automatically at boot-up. How can I make them mount automatically?

When I used Feisty, all partitions were available at boot-up. They are visible in my computer, but now I have to click them once to mount them, and click them once again to browse them in Nautilus. 

This causes Rhythmbox to rescan for new media files every time I reboot (my media files are saved at one of the mentioned partitions).

Any help will be appreciated!

---

### Post by LeighT on 2008-05-10
This thread may answer your problems [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)
But it may cause your system to have shutdown problems if it does go to this thread [http://ubuntuforums.org/showthread.php?t=293513&highlight=cifs+vfs&page=2](http://ubuntuforums.org/showthread.php?t=293513&highlight=cifs+vfs&page=2)

Hope this helps

Leigh

---

### Post by tamoneya on 2008-05-10
post the result of ```
sudo fdisk -l
``` and we will tell you how to add it to /etc/fstab.  This is the file that controls what is mounted automatically.

---

### Post by Joakim Stokland on 2008-05-11
> **tamoneya said:**
> post the result of ```
sudo fdisk -l
``` and we will tell you how to add it to /etc/fstab.  This is the file that controls what is mounted automatically.

Ah, of course! How could I forget fstab? I simply added the partition with mount point and options, and there it was!

Thanks for the hint! :)

---

