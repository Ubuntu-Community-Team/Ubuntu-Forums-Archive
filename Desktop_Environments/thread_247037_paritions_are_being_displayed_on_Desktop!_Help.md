---
title: "paritions are being displayed on Desktop! Help"
date: 2006-08-30
forum: Desktop Environments
---

### Post by ke3pup on 2006-08-30
hi

i have 2 hard disk, one holding windows formatted in ntfs, and the other has linux (ex3) ..etc

when i log in gnome, the partions that i have , including the one that has windows installed, as well as Acronis hidden backup partiton are displayed in desktop! if i unmount them they reappear on desktop after a restart.. is there anyway to get around this? i don't undrestand why is Ubuntu displaying the hard disk that i have windows installed on it in desktop or the Acronis Backup partition(which is hidden in widnwos)? please help. thanx

---

### Post by FuriousLettuce on 2006-08-30
Do you want them to be accessible through linux? If not, go to the terminal and type:

```
sudo cp /etc/fstab /etc/fstab.bak && nano /etc/fstab
```

This will make a backup of your fstab file (where all mounts are kept) and then open the fstab file for editing. There will be a number of lines, with different parameters, and a number of them will begin /dev/hdx (hda, hdb, hdc etc) or /dev/sdx (sda, sdb, sdc etc). The first line will probably be /dev/hdx and then the second column will be a /. This is the hard drive partition that linux is loading as its root partition.

Further down, there will be a number of other lines, saying things such as 'swap', but there will be a pair of lines, probably at the bottom, that contain something along the lines of /mount/windows, or /mnt/windows, or even /media/windows, and another one that looks like it. If you delete these two lines and then reboot, then linux will no longer automount the drives.

If you are worried about making the change, simply post your /etc/fstab here and I will tell you which lines to delete.

---

### Post by CatKiller on 2006-08-31
I believe that Ubuntu automatically places icons to stuff mounted in /media/ on the desktop. If you edit the fstab as FuriousLettuce has suggested and change the mount points rather than removing the lines, the partitions should still be automatically mounted, but not show up on the desktop. You'll have to create directories first, so that the mount points exist.

---

### Post by Omnios on 2006-08-31
From menu go 

 Applications / System tools / configuration editor

 In editor go
 
 apps / nautilus / desktop. 

 Now you have two options if the drives you do not want to show up have entries uncheck them otherwise you can uncheck volumes_visable to make it so mounts do not show

---

