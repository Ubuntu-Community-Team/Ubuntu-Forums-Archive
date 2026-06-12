---
title: "can't boot to windows?"
date: 2009-03-27
forum: General Help
---

### Post by fhydan on 2009-03-27
I've been dual-booting windows and linux for a while. I tried to install sbm but it didn't work so I reinstalled grub on the mbr. However, windows doesn't boot. When I select windows from the boot loader the screen goes black and the machine just reboots. I'm not sure what happened?

```
fhydan@Khwarizmy:/mnt$ sudo fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000000a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1913    15366141   27  Unknown
/dev/sda2   *        1914       29195   219137695+   7  HPFS/NTFS
/dev/sda3           29196       77825   390620475    5  Extended
/dev/sda5           29196       31140    15623181   82  Linux swap / Solaris
/dev/sda6           31141       77825   374997231   83  Linux

```
```

title		Windows Vista/Longhorn (loader)
map (hd0,0) (hd0,1)
map (hd0,1) (hd0,0)
rootnoverify		(hd0,1)
savedefault
makeactive
chainloader	+1
```

any thoughts? I'd appreciate any help.

---

