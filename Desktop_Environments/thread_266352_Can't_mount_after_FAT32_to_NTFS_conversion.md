---
title: "Can't mount after FAT32 to NTFS conversion"
date: 2006-09-27
forum: Desktop Environments
---

### Post by colonelk on 2006-09-27
I have a 12Gig video file that I copied over from the network to my laptop to  work on but since FAT32 doesn't support files that large I had to convert it in Win Vista to NTFS.  Since then when I boot into Ubuntu I can't open/Mount that partition at all.

Any ideas how to make it mountable again?

Thanks in advance

CK

---

### Post by Kateikyoushi on 2006-09-27
List your partition list with
```
sudo fdisk -l
```

Then mount the partition.
```
sudo mount /dev/hdaX /MOUNTDIRECTORY -t ntfs -o nls=utf8,umask=0222
```

Change hdaX to the ntfs hardrive and mountdirectory to the directory where you want to mount it.

If you want it to be permanent have to modify your fstab.

First backup your fstab
```
sudo cp /etc/fstab /etc/fstab_backup
```

Then edit it
```
gksudo gedit /etc/fstab
```

Add to the end the mount command which worked before.
Something like:
```
/dev/hdaX /MOUNTDIRECTORY -t ntfs -o nls=utf8,umask=0222
```

---

### Post by colonelk on 2006-09-27
Many thanks

CK

---

