---
title: "External Encrypted Etch Help"
date: 2008-06-11
forum: Debian
---

### Post by animefan82 on 2008-06-11
I'm currently trying to install Debian on the external drive on the laptop. This is the partition scheme.

2 partitions with mount points "/boot" and "lvm"

2 partitions on lvm; encrypted swap and encrypted ext3 (mount point: /)

Base install is done.

When grub starts after restart I edit the first line:

root (hd2,0) to
root (hd0,0) for obvious reasons.

THEN: The boot sequence can't find the volume group, nor the dm_encrypted swap and ext3, finally ending up in busybox, with very limited commands. What do I do now? how do I change, for instance, the pointers in /boot to point to the external drive (hd0) instead of (hd2), which I suspect the problem is.

PS: When running the same setup in Vbox I don't get the (root (hdx,0)) problem, which is my reason for suspecting bad pointers regarding external drive...
Many thanks in advance.

---

### Post by animefan82 on 2008-06-11
Additional info:
I ran vgchange -a y myvolumegroup (case insensitive) and my 2 logical volumes (root and swap) become active.

running ls /dev/mapper/ gives me
```

myvolumegroup-crypt--root and myvolumegroup-crypt--swap (and control)

```

when exiting initramfs the system fails to continue booting, dropping me right back into initramfs. I thought this was because grub puts the root partition as myvolumegroup-crypt-root_crypt, so I changed this to ...--root and did the same thing, but no go. Then I run 
cryptsetup luksOpen myvolumegroup-crypt--root (and swap)
then exit again, but still, no go... :(

---

### Post by markharding557 on 2008-06-12
does it not ask you for a password for the encrypted volume?mine does

---

