---
title: "Remove mounted devices from the desktop"
date: 2005-10-18
forum: Desktop Environments
---

### Post by fedetxf on 2005-10-18
I have 2 FAT32 partitions mounted automatically and I will soon have a few webdav folders mounted and I don't want to pollute the desktop. Is there any way to have the mounted devices appear in the Places menu, but not in the desktop?

---

### Post by leaber on 2005-10-18
Maybe this helps

[http://ubuntuforums.org/showthread.php?t=66829]("http://ubuntuforums.org/showthread.php?t=66829")

[http://ubuntuforums.org/showthread.php?t=65560]("http://ubuntuforums.org/showthread.php?t=65560")

---

### Post by Kokanee on 2005-10-18
If they are showing on the desktop they are being mounted under the /media directory. They should be under the /mnt directory. Mount them there are they won't show up on the desktop.

---

### Post by fedetxf on 2005-10-18
What about the webdav folders? They are not mounted in /media.

EDIT: Mounting them in /mnt does not change that they appear in the desktop.

Here's my fstab
```

/dev/hda1       /mnt/winc       vfat    rw,user,suid,utf8,umask=002,gid=1001 0 0
/dev/hda5       /mnt/wind       vfat    rw,user,suid,utf8,umask=002,gid=1001 0 0

```
/media shows
```

$ ls /media
cdrom  cdrom0  cdrom1  floppy  floppy0

```
/mnt shows
```

$ ls /mnt/
winc  wind

```

--
Nevermind. I changed my fstab so they don't get mounted automaticlly. I now double click in the drive's icon in the Compuer folder and they drive it mounted on demand.

Still no idea how to control webdav folders, since those are not mounted but  "connected".

---

