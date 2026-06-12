---
title: "I messed up automounting"
date: 2008-10-06
forum: Desktop Environments
---

### Post by ubunny on 2008-10-06
alrightie..

I was hoping to change the automount name from the volume name to the mount name (from Media to /media/disk-1 etc)

So I went to the drive on the deskop, properties, volume and put /media/disk-1 into two blank boxes there.  

Now the drive doesn't mount.  So, how do I remove these settings or where to go to see the gnome settings?  tried .gnome and .gnome2 but nothing.

TIA

---

### Post by onli on 2008-10-06
Hi
I only see a terminal-way to fix this cause I also don't know where gnome keeps these setting. 
Open a Terminal. Create an empty folder in /media, e.g. /media/test ('sudo mkdir /media/test'). Now mount the volume into the folder: e.g 'sudo mount /dev/sda1 /media/test'. You can check if it's /dev/sda1 or anything else by looking at the output of 'sudo blkid'. Now the icon of the volume should reappear on the desktop and you may change your settings.

---

### Post by kpkeerthi on 2008-10-06
See [this post]("http://ubuntuforums.org/showpost.php?p=2477846&postcount=7") for a fix.

[Rename]("https://help.ubuntu.com/community/RenameUSBDrive") the partition's label, so Ubuntu will automount it to a folder named same as the partition's label.

For e.g., if you want ubuntu to automount /dev/sda1 to /media/Storage, label /dev/sda1 to "Storage". The desktop shortcut will also read as Storage, instead of 'XX GB Drive'

---

