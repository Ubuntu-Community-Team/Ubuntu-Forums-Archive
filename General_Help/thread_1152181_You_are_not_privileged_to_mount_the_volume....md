---
title: "You are not privileged to mount the volume..."
date: 2009-05-07
forum: General Help
---

### Post by photon_man62 on 2009-05-07
Lately, since a restart, I seem to get the error in my title when trying to open any of my external hard drives. I got this when trying to configure these "new partitions":

```
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb5': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb5 /media/HP_Pocket_Media_Drive -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb5 /media/HP_Pocket_Media_Drive ntfs-3g force 0 0
```

AND

```
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sde1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sde1 /media/My_Book -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sde1 /media/My_Book ntfs-3g force 0 0
```

This is what I have in my /etc/fstab file:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/sda6 :
UUID=e3f3440f-c893-49b7-bff8-c663b7290b69	/	ext3	relatime,errors=remount-ro	0	1
#Entry for /dev/sda8 :
UUID=102c51d0-21f0-4095-a6c2-f98b520dff8b	/home	ext3	relatime	0	2
#Entry for /dev/sdb5 :
UUID=D234787434785D83	/media/HP_Pocket_Media_Drive	ntfs	defaults,nls=utf8,umask=0222	0	0
#Entry for /dev/sde1 :
UUID=A494843F948415C8	/media/My_Book	ntfs	defaults,nls=utf8,umask=0222	0	0
#Entry for /dev/sda1 :
UUID=12706D07706CF341	/media/sda1	ntfs	defaults,nls=utf8,umask=0222	0	0
#Entry for /dev/sda5 :
UUID=BA7868E37868A03D	/media/sda5	ntfs	defaults,nls=utf8,umask=0222	0	0
#Entry for /dev/sda7 :
UUID=5d387c46-724c-444c-8b6c-9be459a8b426	none	swap	sw	0	0
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0
/dev/scd1	/media/cdrom1	udf,iso9660	user,noauto,exec,utf8	0	0


```

I tried changing

```
#Entry for /dev/sdb5 :
UUID=D234787434785D83	/media/HP_Pocket_Media_Drive	ntfs	defaults,nls=utf8,umask=0222	0	0
#Entry for /dev/sde1 :
UUID=A494843F948415C8	/media/My_Book	ntfs	defaults,nls=utf8,umask=0222	0	0
```

To

```
#Entry for /dev/sdb5 :
UUID=D234787434785D83	/media/HP_Pocket_Media_Drive	ntfs-3g defaults 0 0
#Entry for /dev/sde1 :
UUID=A494843F948415C8	/media/My_Book	ntfs-3g defaults 0 0
```

But every time I restart it tells me to configure these "new partitions" and I get the same two errors I posted at the beginning.

Any ideas? :(

---

### Post by photon_man62 on 2009-05-07
I also seem to be unable to use any of my Windows drives.

---

### Post by photon_man62 on 2009-05-07
Bump :?

---

### Post by photon_man62 on 2009-05-08
I have no idea hwo, but the problem seems to have disappeared.

---

