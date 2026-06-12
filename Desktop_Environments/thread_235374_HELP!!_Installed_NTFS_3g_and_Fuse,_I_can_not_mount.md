---
title: "HELP!! Installed NTFS 3g and Fuse, I can not mount My NTFS Partition"
date: 2006-08-13
forum: Desktop Environments
---

### Post by Chazall1 on 2006-08-13
I am using Ubuntu 6.6 and was following the how toos, for installing the NTFS 3g and Fuse. Both installed without a problem. The problem I have is when I opened the (gksu gedit /etc/fstab) to edit my hda2 NTFS drive. I could not figure out the (Mount Point) This is what I have in the etc/fstab for my NTFS
(/dev/hda2       /media/windows  ntfs-3 silent,umask=0,locale=en_US.utf8 0 0)

And If I get this cleared up, I then followed the rest of the directions:
4. Due to a possible bug in hal, all fuse device (like ntfs-3g ones) are not well recognised by nautilus, and you will not be able to have a link to your drive in the desktop (but you can still browse them from /media/<your mount point> ). To fix that problem, you will have to install a program that will monitor all ntfs-3g device.
Code:

sudo apt-get install ntfs-3g-nautilus-tools

Launch it from the terminal:
Code:

ntfs-3g-monitor &

To launch it at each startup, you will have to add it in your gnome-session.
Navigate to "System > Preference > Sessions". Click on the right-most tab, "Startup Programs".
Create a new entry for ntfs-3g-monitor
Code:

ntfs-3g-monitor


I have rebooted, but I still can not mount my NTFS Drive???  HELP

---

### Post by gerbman on 2006-08-13
This is the fstab line added by the 6.06 installer to mount my NTFS partition:```
/dev/sda2     /media/windows     ntfs     defaults,nls=utf8,umask=007     0     1
```Give it a shot (replace /dev/sda2 with the appropriate partition name).

---

### Post by blackened on 2006-08-17
> This is what I have in the etc/fstab for my NTFS
(/dev/hda2 /media/windows ntfs-3 silent,umask=0,locale=en_US.utf8 0 0)

Did you copy and paste that from fstab? If so it may be a typo as it should read

```
/dev/hda2 /media/windows ntfs-3**g** silent,umask=0,locale=en_US.utf8 0 0
```

Notice the bold 'g'.

---

### Post by buddy_krish on 2006-08-17
Did u Try this??

[https://help.ubuntu.com/community/AutomaticallyMountPartitions]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")

---

