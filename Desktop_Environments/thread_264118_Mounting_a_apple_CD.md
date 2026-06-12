---
title: "Mounting a apple CD?"
date: 2006-09-24
forum: Desktop Environments
---

### Post by morikaweb on 2006-09-24
How do I mount a apple cd in kubuntu? I've tried:
   
    sudo mount -t hfs /dev/hdb /media/cdrom0

which just give me the error:
    
    mount: block device /dev/hdb is write-protected, mounting read-only
    mount: wrong fs type, bad option, bad superblock on /dev/hdb,
    missing codepage or other error
    In some cases useful info is found in syslog - try
    dmesg | tail  or so

The dmesg says:
    
    [17182485.976000] VFS: Can't find a HFS filesystem on dev hdb.
    [17182993.856000] HFS+-fs: unable to find HFS+ superblock
    [17183342.028000] HFS+-fs: unable to find HFS+ superblock
    [17183415.512000] HFS+-fs: unable to find HFS+ superblock
    [17183431.500000] hfs_fs: unable to set blocksize to 1024
    [17183431.500000] VFS: Can't find a HFS filesystem on dev hdb.
    [17183502.640000] hfs_fs: unable to set blocksize to 1024
    [17183502.640000] VFS: Can't find a HFS filesystem on dev hdb.
    [17183686.296000] hfs_fs: unable to set blocksize to 1024
    [17183686.296000] VFS: Can't find a HFS filesystem on dev hdb.

I'm also tried mounting as a hfsplus but it says it does not know what that is. Any help would be appreciated.

---

### Post by alecjw on 2006-09-24
Try just double clicking on it and it should mount.

---

### Post by morikaweb on 2006-09-24
double click what :-s ? I'm trying to mount the disk not open it in a gui.

---

### Post by alecjw on 2006-09-24
Try mounting it specifying iso9660 or udf as the FS.

---

