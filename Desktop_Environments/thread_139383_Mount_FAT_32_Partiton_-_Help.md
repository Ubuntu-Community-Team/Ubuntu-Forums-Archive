---
title: "Mount FAT 32 Partiton - Help"
date: 2006-03-03
forum: Desktop Environments
---

### Post by Replicator on 2006-03-03
Hi guys,

A newbie here to Debien, i use linux for the first time one year ago with Mandrake. I just install a fresh copy of Ubunty on my hardrive. I have dual boot machine but I am trying to mount my FAT32 partion without luck.

Here is my partition looks like

/dev/hda1 My Windows XP partion
/dev/hda3 My Swoop partition (512)
/dev/hda5 My FAT32 Partion

I know that in order to get help here i need to put my etc/fstab information here but I am typing this using Windows. The main problem is that when I am trying to mount my FAT32 partion NOT APPEAR on my etc/fstab also my where my Windows XP is installed not appear.

I don´t know how do I need to do in order to appear my FAT32 partion in the etc/fstab, please I apreciated any help here.

:-?

---

### Post by super on 2006-03-03
just cut and paste this into your /etc/fstab file
```
/dev/hda5  /windows   vfat	  iocharset=utf8,umask=000   0       0
```

---

### Post by xmastree on 2006-03-04
Also, to mount your XP disk (assuming it's ntfs), put this in /etc/fstab:
```
/dev/hda1	/mnt/xpdisk	ntfs	umask=0222	0	0
```

I should add that the mount points must exist before you try to mount the disks there...

e.g.:
sudo mkdir /mnt/xpdisk

---

### Post by akiro.yamamoto on 2006-03-04
These are what the entries should look like in your /etc/fstab file
```

sudo cp /etc/fstab /etc/fstab.bak
sudo gedit /ect/fstab

```
Enter the following into the fstab file (Modify as needed)
/dev/hda5       /media/data     vfat    user,umask=000        0       0
/dev/hda1       /media/win_xp    ntfs    user,ro,umask=0222        0       0

Then save the file and exit gedit.
Enter the following:
```

sudo mkdir /media/win_xp      (Create the win_xp directory)
sudo mkdir /media/data         (Create the data directory)
sudo umount /dev/hda1         (Unmount the WinXP Partition)
sudo umount /dev/hda5         (Unmount the Fat32 Partition)
sudo mount -a      (Mount all unmounted drives using the info from fstab)

```

---

