---
title: "Moving Home to a Windows Drive?"
date: 2009-06-12
forum: General Help
---

### Post by manekineko2 on 2009-06-12
I'd like to move my /home directory to an NTFS partition with existing data, ideally to a subdirectory off of the root.  Is such a thing possible, or would I have to dedicate a new partition solely to this?

My setup is I have a Windows setup running off of a hard drive.  The hard drive is split into two partitions, one called Windows (for Windows and applications), and one called Data (for data files).  

I also have a bootleg SSD made from a CompactFlash adapter installed in my computer.  Ubuntu is installed on this.  Currently I have my home on this as well.

Is there any way I could move my home directory to Data/UbuntuHome?  All of the tutorials I've managed to find seem to require dedicating an entire partition to the Home directory, which isn't really what I want, and doesn't really make a lot of sense because I've essentially already got that setup for my Windows install.

---

### Post by statistic on 2009-06-12
First put the windows partition in your fstab:
[http://markhill.me.uk/articles/mounting_windows_partitions/](http://markhill.me.uk/articles/mounting_windows_partitions/)

Once it's there it'll be a folder you can access normally at your chosen path. You can them replace your home folder with a symbolic link , and point it to somewhere on the mounted windows partition to be your home folder.

EDIT: There are certain security issues with this, so keep reading to the thread for more details.

---

### Post by ad_267 on 2009-06-12
I'm not sure if putting your home directory on an NTFS drive is a good idea as there could be permission problems. I would leave the home directory on the ubuntu partition, but make your Documents, Pictures, Music directories etc symbolic links to directories on your data drive.

---

### Post by Villiam on 2009-06-12
I dont know if it fits your requirements but you can always try using Wubi to install Ubuntu. It will install it in your NTFS partition without any hassle. [http://wubi-installer.org/](http://wubi-installer.org/)

[ubuntu]("http://www.linux-archive.org/ubuntu-user/")

---

### Post by cariboo on 2009-06-12
You can't put your home folder on an ntfs partition, as you can't set the permissions properly, as ntfs doesn't use linux permissions. Your installation will not work properly if you try. You can put your home directory anywhere as long as the partition is formated as ext2/3/4.

---

### Post by statistic on 2009-06-12
> **ad_267 said:**
> I'm not sure if putting your home directory on an NTFS drive is a good idea as there could be permission problems. I would leave the home directory on the ubuntu partition, but make your Documents, Pictures, Music directories etc symbolic links to directories on your data drive.

I agree with ad_267 on this. This would keep you from running out of space you have on the external, Just make sure you save things of decent size in the symbolic links, and all the configuration will still be hidden folders in with proper permissions. So there will be permissions where permissions matter. That should overcome the permissions issues mentioned by others.

---

### Post by sedawk on 2009-06-12
I think you might get into lots of trouble with tools that want
to set linux permissions in the home directory and fail because
it is NTFS.

1) You can try to keep your home directory at minimum size and store
   everything else on the NTFS partition (with or without symbolic links
   that simplify your life

2) It should be possible to create a big file in the NTFS partition
   (wherever you like) and mount that file as a "loop device" 
   like a real disk partition to /home or /home/<your_user>.
   But I'm not sure this can be done automatically (/etc/fstab) because
   to "loop-mount" the file (as partition) from a NTFS partition that
   NTFS partition must be mounted first (so is it enough to have that
   line before the "loop-line" in /etc/fstab? Never tried ...)


3) Make a backup of your disk to an external HDD (e.g with partimage)
   and try to resize (shrink) the data partition to make space
   for a new partition on the disk (to store /home or /home/<your_user>)

---

### Post by manekineko2 on 2009-06-12
Wow thanks for all the great responses!

I guess I'll follow the advice on the symbolic links.  It's not my ideal resolution, but it works.

Thanks again all!

---

