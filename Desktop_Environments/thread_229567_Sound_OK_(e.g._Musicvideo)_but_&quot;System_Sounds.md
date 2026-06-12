---
title: "Sound OK (e.g. Music/video) but &quot;System Sounds&quot; not working"
date: 2006-08-04
forum: Desktop Environments
---

### Post by Doctoxic on 2006-08-04
Hi all

I am using dapper/gnome

I have a bit of a problem in  that sound work OK (e.g. Music/video) but "System Sounds" not working e.g. the sound on boot up etc

I have an ASus mobo with nvidia sound drivers installed which are OSS - (system sounds used to work under my old soundblaster card (alsa) before i changed to the onboard sound).

I googled and found these instructions but no luck:
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_configure_sound_to_work_properly_in_GNOME](http://easylinux.info/wiki/Ubuntu_dapper#How_to_configure_sound_to_work_properly_in_GNOME)

As i said my sound is OSS (using Nvidia sound drivers with onboard mobo sound) - is this why these instructions aren't helping - and if so any idea how to get it working?

i have an oss.conf file where the esd one is but it only contains:
OSSLIBDIR=/usr/lib/oss

Many thanks

Diss

PS not sure if this makes any difference but this is a dual boot system with winXP and there is a Xi-Fi sound card installed that WinXP uses - my Linux uses the onboard sound


EDIT my fstab looks like this
/dev/sdb4       /               reiserfs notail,noatime  0       1
/dev/sdb2       /boot           ext2    defaults        0       2
/dev/sdb3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
/dev/hda1       /mnt/hda1  vfat    iocharset=utf8,umask=000   0       0
/dev/sda1	/media/windows  ntfs    nls=utf8,umask=0222 0       0
/dev/sda5       /media/winstuff  ntfs    nls=utf8,umask=0222 0       0

---

