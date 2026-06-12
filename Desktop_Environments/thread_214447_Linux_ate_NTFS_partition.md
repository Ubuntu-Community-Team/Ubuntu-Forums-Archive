---
title: "Linux ate NTFS partition?"
date: 2006-07-12
forum: Desktop Environments
---

### Post by zrothe on 2006-07-12
I discovered this last week when I went to retrieve a file from my NTFS partition and found my mount to be an empty folder.

[QUOTE=mounting]aaron@knapp:~$ sudo mount /dev/sda1 /media/windows -t ntfs -r
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
[/QUOTE]

[QUOTE=dmesg | tail][17180739.384000] NTFS-fs warning (device sda1): is_boot_sector_ntfs(): Invalid boot sector checksum.
[17180739.384000] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17180739.384000] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17180739.384000] NTFS-fs error (device sda1): ntfs_fill_super(): Not an NTFS volume.
[/QUOTE]

Is there any fixing this? If not I've lost some important stuff. Thanks.

---

### Post by Jagot on 2006-07-12
You could try mounting like this and see if it gives the same error:

```
sudo mount /dev/sda1 /media/windows/ -t ntfs -o umask=0222
```

---

### Post by zrothe on 2006-07-12
> **Jagot said:**
> You could try mounting like this and see if it gives the same error:

```
sudo mount /dev/sda1 /media/windows/ -t ntfs -o umask=0222
```

Yeah, same error:

> aaron@knapp:~$ sudo mount /dev/sda1 /media/windows/ -t ntfs -o umask=0222
Password:
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


---

