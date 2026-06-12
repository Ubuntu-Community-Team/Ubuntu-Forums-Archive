---
title: "Using ubuntu to save files from Windows"
date: 2009-03-06
forum: General Help
---

### Post by Martinuz on 2009-03-06
Hi!

Been trying to recover files from my unbootable Vista machine,.. using this article:

[http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/#comment-68247](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/#comment-68247)

I seem to bee one of the lucky ones because i find all my files. My problem is that none of the usb-drives i want to transfer files to (200 gigs of important creative projects), seems to be found automaticly,.. Would be much appriciated with any help on getting ubuntu to see them!

MaRTin

(tried a usb memory stick and Ubuntu found that, but none of my two usb drives)

---

### Post by taurus on 2009-03-06
Make sure the drive is on and plug in.  Then, open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
dmesg | tail
sudo fdisk -l
df -h
```

---

### Post by Martinuz on 2009-03-07
Tanx alot Taurus!

Here is the output,...


ubuntu@ubuntu:~$ dmesg | tail
[   66.544217] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   66.544231] Bluetooth: BNEP filters: protocol multicast
[   66.679393] Bridge firewalling registered
[   66.679706] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   74.805180] b44: eth0: Link is up at 100 Mbps, full duplex.
[   74.805195] b44: eth0: Flow control is off for TX and off for RX.
[   74.976229] NET: Registered protocol family 17
[  291.826573] NET: Registered protocol family 10
[  291.829255] lo: Disabled Privacy Extensions
[  302.388016] eth0: no IPv6 routers present
ubuntu@ubuntu:~$ 

sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x48000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8        1313    10490352+   7  HPFS/NTFS
/dev/sda3   *        1313       38914   302034625    7  HPFS/NTFS
ubuntu@ubuntu:~$ 

ilesystem            Size  Used Avail Use% Mounted on
tmpfs                 1.5G  2.0M  1.5G   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 1.5G  2.0M  1.5G   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  100K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  2.8M  1.5G   1% /dev
tmpfs                 1.5G  104K  1.5G   1% /dev/shm
rootfs                1.5G   38M  1.5G   3% /
/dev/scd0             699M  699M     0 100% /cdrom
/dev/loop0            676M  676M     0 100% /rofs
tmpfs                 1.5G   12K  1.5G   1% /tmp
ubuntu@ubuntu:~$

---

### Post by Martinuz on 2009-03-07
Here is what i got from the new commands...

ubuntu@ubuntu:~$ lsusb
Bus 002 Device 004: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 002 Device 003: ID 413c:3016 Dell Computer Corp.
Bus 002 Device 002: ID 0582:0033 Roland Corp. EDIROL PCR
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ubuntu@ubuntu:~$
ubuntu@ubuntu:~$ demsg | tail

bash: demsg: command not found


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x48000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8        1313    10490352+   7  HPFS/NTFS
/dev/sda3   *        1313       38914   302034625    7  HPFS/NTFS
ubuntu@ubuntu:~$

---

