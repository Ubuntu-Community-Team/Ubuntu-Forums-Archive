---
title: "I can't mount anything"
date: 2006-06-05
forum: Desktop Environments
---

### Post by george_apan on 2006-06-05
I had this problem after a dist-upgrade of breezy to dapper and I thought that maybe after a clean install of dapper it would work. I used the xubuntu live CD for the installation and, well, I still can't mount any device. :(

If I try to mount my laptop's internal CD-ROM I get a "could not execute pmount" error thrown at me. I was able to mount this drive by using "sudo mount" as it is already in fstab. Still I don't get why it can't mount automatically as it did in breezy.

When I attach my external HD (reiserfs) I get an icon on my xfce desktop but when I try to mount it I get the same "could not execute pmount" error. No only that but the CPU hits 100% and doesn't stop. The mount process keeps working forever and I can't even reboot or shutdown without everything hanging. If I put the appropriate entry in fstab for /dev/sda1 (although I know I should not do that and that it should mount without it) I can't mount it with sudo as I did with the internal CD-ROM. The mount command hangs and I'm left with CPU at 100% and not able to shutdown or reboot again. The "dmesg | grep sda" I get is this:
```
[4300605.853000] SCSI device sda: 490234752 512-byte hdwr sectors (251000 MB)
[4300605.854000] sda: assuming drive cache: write through
[4300605.920000] SCSI device sda: 490234752 512-byte hdwr sectors (251000 MB)
[4300605.920000] sda: assuming drive cache: write through
[4300605.920000]  sda: sda1
[4300605.947000] sd 1:0:0:0: Attached scsi disk sda
[4300665.658000] ReiserFS: sda1: found reiserfs format "3.6" with standard journal
[4300681.809000] ReiserFS: sda1: using ordered data mode
[4300681.832000] ReiserFS: sda1: journal params: device sda1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[4300681.841000] ReiserFS: sda1: checking transaction log (sda1)

```
And it just stops there. There is no way to kill the mount process as far as I can tell. Note that this is not an HD problem as it mounts with no problems under breezy.

---

### Post by george_apan on 2006-06-06
I finally gave up. After another mount try the system froze and then refused to boot with no error messages. I reinstalled breezy, I simply can't work without using external devices. I won't try another upgrade to dapper unless I see that others who have the same problems are over them. Too bad, I was expecting too much from dapper, but I can't say that I can recommend it to anyone.

---

### Post by GlennB on 2006-06-06
I'll be watching with interest - I've had odd problems with 'mount' as well, but they are not the same as yours. for some weird reason during my upgrade to dapper, support for smbfs disappeared from my install.

Under 5.10, I mounted (from fstab) a samba share on a separate server. After the upgrade to 6.06 this stopped working.

Doing 
```

mount -t smbfs //server/share /mnt/somewhere
```

got me errors claiming 'bad superblock, wrong filesystem' etc. It turns out
that fixing the problem was as simple as doing:

```
apt-get install smbfs
```

as smbfs (and therefore smbmount) had mysteriously been uninstalled, despite the package managers claiming that the samba client packages were all present.

It's probably unrelated, but who knows...

Regards,

Glenn.

---

### Post by george_apan on 2006-06-07
Yeah, I had the same problem too with the upgrade and smbfs but it's not related to the external devices mount problem I have. This happens also with a new installation. Thanks anyway.

---

