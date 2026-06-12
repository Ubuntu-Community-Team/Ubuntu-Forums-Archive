---
title: "Not mounting secured partition with swap"
date: 2018-08-21
forum: Desktop Environments
---

### Post by driversti on 2018-08-21
Hi all,

I've got a work laptop Lenovo P51. There is Win10 on a secured partition. I installed Ubuntu 18.04 on a secured partition as well. Also, I've created a secured partition for swap, but it doesn't mount.
The launch time is about 2 minutes what is very annoying

here is **sudo blkid output** and there is no a secured partition for swap (I supposed it should looks like **/dev/mapper/nvme0n1p6**)

```

$ sudo blkid                                       
/dev/mapper/nvme0n1p7_crypt: UUID="94fe7730-b54e-43a6-be1c-ec4c1fcec084" TYPE="ext4"
/dev/nvme0n1p1: LABEL="BOOT" UUID="56A4-3F33" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="b2acdb69-298e-4720-8368-30a86df0d055"
/dev/nvme0n1p4: LABEL="DATA" UUID="160E3B620E3B3A57" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="e05129b9-f57e-48b3-8502-ad7129883615"
/dev/nvme0n1p5: UUID="95aa2c8c-2cd1-4fef-8dc3-c93a896e9f15" TYPE="ext4" PARTUUID="f12911aa-86cc-4d9a-8117-39fd5a31bd8e"
/dev/nvme0n1p7: UUID="20adda12-da97-4c79-af97-cb69a7a4af00" TYPE="crypto_LUKS" PARTUUID="26e3155a-aee1-4185-82d2-a4d41d6cee6c"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/loop12: TYPE="squashfs"
/dev/loop13: TYPE="squashfs"
/dev/loop14: TYPE="squashfs"
/dev/loop15: TYPE="squashfs"
/dev/nvme0n1: PTUUID="71954aea-d40f-480d-ad82-e574d4960a4d" PTTYPE="gpt"
/dev/nvme0n1p2: PARTLABEL="Microsoft reserved partition" PARTUUID="db7c9553-7b2e-4b8d-acd4-b04a66af3bc2"
/dev/nvme0n1p3: PARTLABEL="Basic data partition" PARTUUID="cc57510d-4af0-4c72-9233-e2acf8b439d6"
/dev/nvme0n1p6: PARTUUID="00d5b8ac-276c-4662-acfc-16f9b3eaa098"

```

and **fstab** content:
```

$ sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
UUID=94fe7730-b54e-43a6-be1c-ec4c1fcec084 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/nvme0n1p5 during installation
UUID=95aa2c8c-2cd1-4fef-8dc3-c93a896e9f15 /boot           ext4    defaults        0       2
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=56A4-3F33  /boot/efi       vfat    umask=0077      0       1
# /media/DATA was on /dev/nvme0n1p4 during installation
UUID=160E3B620E3B3A57 /media/DATA     ntfs    defaults,umask=007,gid=46 0       0
#/dev/mapper/nvme0n1p6_crypt none            swap    sw              0       0

```

Could anyone help me to mount swap on startup?

---

