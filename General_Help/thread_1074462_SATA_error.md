---
title: "SATA error"
date: 2009-02-19
forum: General Help
---

### Post by helai on 2009-02-19
I am using ubuntu 8.04.2  
2.6.24-23-generic
PATA 160G + SATA 320G

I install ubuntu on 160G(PATA) and download files to 320G(SATA)
the problem is vuze will always be shut down by OS saying disk read error-open fails(file will be download to SATA)


for drives,more detail as below
```
lenovo@linux:~$ sudo fdisk -l
[sudo] password for lenovo: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe4ae6f91

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          17      136521   83  Linux
/dev/sda2              18       19457   156151800    f  W95 Ext'd (LBA)
/dev/sda5            7862       16837    72099688+  83  Linux
/dev/sda6              18         304     2305264+  82  Linux swap / Solaris
/dev/sda7             305        5002    37736653+  83  Linux
/dev/sda8            5003        7861    22964886   83  Linux
/dev/sda9           16838       19457    21045118+   b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd33c5ad4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3916    31455238+   7  HPFS/NTFS
/dev/sdb2            3917       38913   281113402+   f  W95 Ext'd (LBA)
/dev/sdb5            3917        7832    31455238+   7  HPFS/NTFS
/dev/sdb6            7833       27318   156521263+   7  HPFS/NTFS
/dev/sdb7           27319       37518    81931468+  83  Linux
/dev/sdb8           37519       38913    11205306   bc  Unknown

```

and if I go to log file,it shows me

```
Feb 19 20:45:46 linux -- MARK --
Feb 19 20:58:27 linux kernel: [ 5601.563353] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Feb 19 20:58:27 linux kernel: [ 5601.563373] ata3.00: cmd 25/00:00:dd:7f:b1/00:01:1e:00:00/e0 tag 0 dma 131072 in
Feb 19 20:58:27 linux kernel: [ 5601.563375]          res 40/00:01:00:4f:c2/84:00:00:00:00/00 Emask 0x4 (timeout)
Feb 19 20:58:27 linux kernel: [ 5601.563384] ata3.00: status: { DRDY }
Feb 19 20:58:32 linux kernel: [ 5606.597847] ata3: port is slow to respond, please be patient (Status 0xd0)
Feb 19 20:58:37 linux kernel: [ 5611.579488] ata3: device not ready (errno=-16), forcing hardreset
Feb 19 20:58:37 linux kernel: [ 5611.579496] ata3: soft resetting link
Feb 19 20:58:37 linux kernel: [ 5611.825641] ata3.00: configured for UDMA/33
Feb 19 20:58:37 linux kernel: [ 5611.825675] ata3: EH complete
Feb 19 20:58:37 linux kernel: [ 5611.851479] sd 2:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
Feb 19 20:58:37 linux kernel: [ 5611.968890] sd 2:0:0:0: [sdb] Write Protect is off
Feb 19 20:58:37 linux kernel: [ 5611.968902] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
```

any advices are welcome!
helai

---

### Post by taurus on 2009-02-19
Which partition on /dev/sdb did you try to save your download to since you have four partitions plus an unknown?

---

### Post by helai on 2009-02-19
For 320G hard drive ,it has three NTFS partitions,and one EXT3(sdb7),one hidden FAT32 partition(marked as unknown)
now I want to download file to sdb7.
btw:
motherboard :ASUS p4p800-x firmware:1004

and after I google the internet,I find somebody say upgrade the BIOS,somebody prefer upgrading the kernel. but as you know ,none of firmware is stable for p4p800-x even up to now,and upgrade the kernel is also difficult for me if let me run it without "apt-get" help

Helai

---

### Post by Yellow Pasque on 2009-02-19
> I find somebody say upgrade the BIOS
That is one possiblity, although none of Asus' BIOS release notes mention SATA fixes.

Your motherboard only supports SATA 150MB/s. What model hard disk do you have? If it's a SATA 300MB/s drive, then you may need to set a jumper on the drive to force SATA 150MB/s mode.

---

### Post by taurus on 2009-02-19
If you want to change the ownership of /dev/sdb7 (linux) from root to your login name, lenovo, you would do something like

```
sudo chown -R lenovo:lenovo /media/sdb7
```
_Assuming_ you have mounted /dev/sdb7 to /media/sdb7.

---

### Post by helai on 2009-02-20
> **Temüjin said:**
> That is one possiblity, although none of Asus' BIOS release notes mention SATA fixes.

Your motherboard only supports SATA 150MB/s. What model hard disk do you have? If it's a SATA 300MB/s drive, then you may need to set a jumper on the drive to force SATA 150MB/s mode.

I think you are right,this night I will take a try
my SATA drive is seagate 7200.11 ,so it should be SATAII.

---

