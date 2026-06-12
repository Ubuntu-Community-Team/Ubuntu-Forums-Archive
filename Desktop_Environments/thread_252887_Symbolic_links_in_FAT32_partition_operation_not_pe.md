---
title: "Symbolic links in FAT32 partition: operation not permitted"
date: 2006-09-07
forum: Desktop Environments
---

### Post by FakeOutdoorsman on 2006-09-07
I'm attempting to share data between my dual boot Ubuntu / Windows installation on a FAT partition.  I made two Firefox profiles and want to share the bookmarks and other files by creating symbolic links:
```
sudo ln -s /media/windows/Mozilla_Profiles/windows/bookmarks.html .
```

I deleted the corresponding files in the target directory to prevent conflict.  When I type the above code in the directory I want the symbolic link I get an error: *Operation not permitted*.

I looked at my fstab and was using the following entry from [ubuntuguide.org]("http://ubuntuguide.org") to gain read/write access to the FAT partition:
```
/dev/sda5    /media/windows vfat  iocharset=utf8,umask=000  0    0
```

The files on the partition were owned by root in the root group.  I added uid and gid to the fstab and made myself owner and group and remounted the partition.  I still got the same *Operation not permitted* error and I assume adding uid and gid might screw up Windows access.

Everything works fine in Windows, but I can't create symbolic links in Ubuntu.  I searched the forum and didn't find much.  I don't know how to make this work.  Any ideas?

---

### Post by cat5 on 2006-09-08
You can not make a Symbolic link on a Fat32 drive.

This won't work. try copying the profile instead.

---

### Post by FakeOutdoorsman on 2006-09-08
Curses!  I should have known.  Stupid archiac FAT!  I was able to share the same Thunderbird profile on the FAT32 partition, but I use some Firefox extensions that aren't compatible between Ubuntu and Windows.

---

