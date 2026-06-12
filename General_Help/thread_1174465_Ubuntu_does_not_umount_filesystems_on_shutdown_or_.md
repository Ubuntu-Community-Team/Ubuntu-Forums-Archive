---
title: "Ubuntu does not umount filesystems on shutdown or restart"
date: 2009-05-30
forum: General Help
---

### Post by ctrl0l on 2009-05-30
I have Ubuntu 9.04
I t seems it doesn't umount the filesystems (ReiserFS) on shutdown or restart.
There is no matter if I click on Gnome Shutdown/Restart button, or I type "shutdown -r now" - after restart, I see the following message in console:
"Filesystem is not clean" and the system forces ReiserFS's checking process.

I tried to figure out the reason, but no success.
I was not able to force shutdown process to log what it does; umount related services seem to be configured properly:
```

umountfs                  0:on   1:off  2:off  3:off  4:off  5:off  6:off
umountnfs.sh              0:on   1:off  2:off  3:off  4:off  5:off  6:off
umountroot                0:on   1:off  2:off  3:off  4:off  5:off  6:off

```Could someone help with this issue?

---

### Post by dcstar on 2009-05-31
> **ctrl0l said:**
> I have Ubuntu 9.04
I t seems it doesn't umount the filesystems (ReiserFS) on shutdown or restart.
There is no matter if I click on Gnome Shutdown/Restart button, or I type "shutdown -r now" - after restart, I see the following message in console:
"Filesystem is not clean" and the system forces ReiserFS's checking process.

I tried to figure out the reason, but no success.
I was not able to force shutdown process to log what it does; umount related services seem to be configured properly:
```

umountfs                  0:on   1:off  2:off  3:off  4:off  5:off  6:off
umountnfs.sh              0:on   1:off  2:off  3:off  4:off  5:off  6:off
umountroot                0:on   1:off  2:off  3:off  4:off  5:off  6:off

```Could someone help with this issue?

Post your /etc/fstab

---

### Post by ctrl0l on 2009-05-31
> **dcstar said:**
> Post your /etc/fstab

Here is it:

```
proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=32b994f9-7734-400a-9708-501705ef6fa5 / reiserfs notail,relatime 0 1
# Entry for /dev/sda5 :
UUID=a1acb64d-4cb2-4400-832a-79d73c613b18 /home reiserfs relatime 0 2
# Entry for /dev/sda8 :
UUID=c13a0612-3880-429b-8d5f-049ada9109dc /opt reiserfs relatime 0 2
# Entry for /dev/sda10 :
UUID=62617ffc-5a46-43a3-b90f-e1c3802e275a /other reiserfs relatime 0 2
# Entry for /dev/sda7 :
UUID=9bf840d0-d8ec-4aee-87ed-8ef82d20c571 /usr reiserfs relatime 0 2
# Entry for /dev/sda6 :
UUID=8c0887b4-470f-4dd6-9ff8-0e16ae3305c0 /var reiserfs relatime 0 2
# Entry for /dev/sda9 :
UUID=c3eb5791-fd6a-492d-94f3-ae0a2f9024d8 /work reiserfs relatime 0 2
# Entry for /dev/sda2 :
UUID=2962f33a-f3df-44c9-a2dd-1cb2216f117f none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

# /dev/sda4
UUID=ECFC0A72FC0A36FC /windows ntfs-3g defaults,locale=en_US.UTF-8 0 0
```

Thanks,
Iliyan

---

### Post by Lucio01 on 2010-08-07
Hi,
i've the same problem with Ubuntu 10.4. reiser filesystems, ext3 and ext4 as well.
It seems that despite the fact that the umount scripts are in the different rcX.d; they are not called.

If i manually umount the different aux filesystems, only / is not clean at next boot. 

Something is strange to me, i've no sequence (only 3 levels)  in the rcx.d:
only S01halt, S01sendsigs, S01umountfs, S01umountnfs.sh, S01umountroot, S01unattended-upgrades, S02urandom, S02wpa-ifupdown, S35networking


my fstab (just in case it may help)

```

proc            /proc           proc    defaults        0       0
/dev/sda6  none            swap    sw              0       0

UUID=74784db3-d8cd-4cc0-98b3-0b574b67aefa  /            reiserfs        notail,relatime 0       1
UUID=9cf03f60-8bc3-4fcf-a15d-5cf4205aa67a  /home        reiserfs        relatime        0       1
UUID=680ede56-4375-40aa-bf56-7b2862aa210b  /mnt/VBoxes  auto            user             0 1
UUID=3e94453c-d353-4bbd-93c7-e8f01f3d7af4  /mnt/gentoo  reiserfs        noauto,notail,relatime 0       1
UUID=8F0D-4126                             /mnt/D       vfat            noauto,user             0 0
UUID=60dee998-d605-46a3-a357-e39282986790  /www         reiserfs        noatime         0 1
UUID=eb90d9d4-b5fc-4aa3-a877-76a80c9c1cb2  /mnt/Pictures ext4           noauto,user             0       1

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


```

Lucio

---

