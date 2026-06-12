---
title: "Help with gparted"
date: 2009-03-14
forum: General Help
---

### Post by terpdan on 2009-03-14
I attempted to resize(shrink) my windows vista partition in hopes of growing my ubuntu partion.

I used the gparted live cd and resized the vista partition to 80gb.
the operation seemed to complete ok but then i had two problems

first i cannot reboot vista (by selecting longhorn loader from the grub boot screen), screen says Starting up    and goes no further

second gparted won't let me grow the ubuntu partition into the unallocated space... 

attached is screenshot from gparted (run from ubuntu after reboot)


[ATTACH]106401[/ATTACH]

---

### Post by taurus on 2009-03-14
You cannot resize Ubuntu partition while you are running it.  Therefore, you must boot into the LiveCD and expand /dev/sda2 (extended partition) to take up that unallocated space.  Then, you can now expend /dev/sda5 to use that space.

---

### Post by drs305 on 2009-03-14
For the second problem, you must first expand the extended partition (sda2) to incorporate the unallocated space. Do this from the LiveCD. Once this space is within the extended partition, you can expand your ubuntu partition (sda5) to absorb that space. Since you will be adding space from left, the operations will probably take some time to complete. 

Make sure you back up important data before moving any partitions.

---

### Post by terpdan on 2009-03-14
yes i know that, just opened in ubuntu so i could send the screenshot. won't let me expand into unallocated from gparted live cd.

---

### Post by taurus on 2009-03-14
Remember to unmount the swap partition (highlight /dev/sda6 and click the right button -> swapoff).

---

### Post by terpdan on 2009-03-14
ok i'll give that a try

---

### Post by terpdan on 2009-03-14
yes, expanding sda2 first let me grow sda5 and yes it looks like it will take a while.

any ideas on the problem with the vista partition. I could reinstall, it was a fresh install, so i'm not losing much, but would i need to figure out how to keep from messing up grub loader.

---

### Post by drs305 on 2009-03-15
> **terpdan said:**
> any ideas on the problem with the vista partition. I could reinstall, it was a fresh install, so i'm not losing much, but would i need to figure out how to keep from messing up grub loader.

I don't dual boot vista so I am not familiar with how it appears in grub. Is vista in the grub menu referenced via UUID? You might check the grub menu to make sure the referenced partition in grub correctly references the proper UUID or /dev/sdXX. 

You can check the UUIDs with:
```
sudo blkid
```

If this doesn't help you might post your menu.list so others can take a look at it.

---

### Post by terpdan on 2009-03-15
here is the menu.lst 

title Ubuntu 8.10, kernel 2.6.27-11-generic
uuid f0990563-a458-4925-a642-69beada642ab
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=f0990563-a458-4925-a642-69beada642ab ro xforcevesa quiet splash
initrd /boot/initrd.img-2.6.27-11-generic
quiet

title Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid f0990563-a458-4925-a642-69beada642ab
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=f0990563-a458-4925-a642-69beada642ab ro xforcevesa single
initrd /boot/initrd.img-2.6.27-11-generic

title Ubuntu 8.10, kernel 2.6.27-9-generic
uuid f0990563-a458-4925-a642-69beada642ab
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=f0990563-a458-4925-a642-69beada642ab ro xforcevesa quiet splash
initrd /boot/initrd.img-2.6.27-9-generic
quiet

title Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid f0990563-a458-4925-a642-69beada642ab
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=f0990563-a458-4925-a642-69beada642ab ro xforcevesa single
initrd /boot/initrd.img-2.6.27-9-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic
uuid f0990563-a458-4925-a642-69beada642ab
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=f0990563-a458-4925-a642-69beada642ab ro xforcevesa quiet splash
initrd /boot/initrd.img-2.6.27-7-generic
quiet

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid f0990563-a458-4925-a642-69beada642ab
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=f0990563-a458-4925-a642-69beada642ab ro xforcevesa single
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, memtest86+
uuid f0990563-a458-4925-a642-69beada642ab
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows Vista/Longhorn (loader)
root (hd0,0)
savedefault
makeactive
chainloader +1

---

### Post by terpdan on 2009-03-15
and the sudo blkid

/dev/sda1: UUID="826C547A6C546B45" TYPE="ntfs"
/dev/sda5: UUID="f0990563-a458-4925-a642-69beada642ab" TYPE="ext3"
/dev/sda6: TYPE="swap" UUID="950e52eb-9722-4294-a5fc-c6e18b8235df"

---

### Post by terpdan on 2009-03-15
I ran boot_info_script and it looks like some confusion over where the boot sector is. any suggestions?

============================= Boot Info Summary: ==============================

=> Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive
in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows Vista
Boot sector info: According to the info in the boot sector, sda1 starts
at sector 2048. But according to the info from fdisk,
sda1 starts at sector 63.
Operating System: Windows Vista
Boot files/dirs: /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________ _______________________

File system: Extended Partition
Boot sector type: -
Boot sector info:

sda5: __________________________________________________ _______________________

File system: ext3
Boot sector type: -
Boot sector info:
Operating System: Ubuntu 8.10
Boot files/dirs: /boot/grub/menu.lst /etc/fstab

sda6: __________________________________________________ _______________________

File system: swap
Boot sector type: -
Boot sector info:

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ __________________________________________________ ___

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000abf88

Partition Boot Start End Size Id System

/dev/sda1 * 63 163,846,934 163,846,872 7 HPFS/NTFS
/dev/sda2 163,846,935 625,137,344 461,290,410 5 Extended
/dev/sda5 163,846,998 619,900,154 456,053,157 83 Linux
/dev/sda6 619,900,218 625,137,344 5,237,127 82 Linux swap / Solaris

---

### Post by terpdan on 2009-03-15
I ended up reinstalling vista, no biggee other than the time, it was barely used since install. 

used quick start option at [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) to get grub working again

i only keep windows for two things: go-to-meeting and tax software

thanks for help

---

