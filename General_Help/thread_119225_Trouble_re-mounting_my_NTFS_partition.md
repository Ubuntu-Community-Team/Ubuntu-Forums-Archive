---
title: "Trouble re-mounting my NTFS partition"
date: 2006-01-19
forum: General Help
---

### Post by three_sixteen on 2006-01-19
Long story short, I had to reinstall Windows to install SP2.  Windows being the whore that it is hijacked my MBR and so I had to reinstall GRUB using a live CD.  Afterwards my NTFS volume wouldn't mount anymore.  

fdisk -l:
```
/dev/hda1   *           1        8287    66565296    7  HPFS/NTFS

```

/etc/fstab line:
```
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222        0       0

```

```
austin@threesixteen:/$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

```
[4295358.623000] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[4295358.623000] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[4295358.623000] NTFS-fs error (device hda1): ntfs_fill_super(): Not an NTFS volume.

```

Where have I gone wrong?

EDIT: Son of a bitch, I can't boot into Windows anymore with Grub, I get the feeling that my NTFS partition is borked now.

---

### Post by three_sixteen on 2006-01-19
Bumping, looking for some advice.

---

### Post by sampoerna on 2006-01-19
try to mount it manually with
*sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222*

check this site for more details:
[http://ubuntuguide.org/]("http://ubuntuguide.org/")

i tried the mount drive on boot-up & manually, both works for me.

hope these help

---

### Post by three_sixteen on 2006-01-19
[QUOTE=sampoerna]try to mount it manually with
*sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222*

check this site for more details:
[http://ubuntuguide.org/]("http://ubuntuguide.org/")

i tried the mount drive on boot-up & manually, both works for me.

hope these help[/QUOTE]

**Thanks** for the reply however it still returns the same error :(
```

mount: wrong fs type, bad option, bad superblock on /dev/hda1,
```

---

