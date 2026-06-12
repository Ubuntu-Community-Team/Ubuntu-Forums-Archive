---
title: "[SOLVED] NTFS Partition cannot be mounted"
date: 2009-01-02
forum: General Help
---

### Post by deamon_knight on 2009-01-02
I'm Running Ubuntu 8.10, fully updated. Worked earlier today, I had to tinker with Wine, rebooted, and now I cannot mount the XP partition. Dual boot setup, Ubuntu on one half, XP on the other, both OSes load normally. The XP partition shows in "Places" but when selected I get "Invalid mount option when attempting to mount the volume." application I was running in Wine reside in Ubuntu partition, not XP.

I also noticed that while I C/P that error I got another DBUS error:

"DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

Any advice?

---

### Post by dcstar on 2009-01-02
> **deamon_knight said:**
> I'm Running Ubuntu 8.10, fully updated. Worked earlier today, I had to tinker with Wine, rebooted, and now I cannot mount the XP partition. Dual boot setup, Ubuntu on one half, XP on the other, both OSes load normally. The XP partition shows in "Places" but when selected I get "Invalid mount option when attempting to mount the volume." 
......
Any advice?

Post the contents of /etc/fstab

---

### Post by deamon_knight on 2009-01-03
Duh, I fired off that post in a rush.

FSTAB:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=879f5076-66fe-4504-a62c-f45d26ccd5b7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=fbcad461-4678-4b87-b541-0abe147f5092 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
,

Results of FDISK -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7029465b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         445       16381   128013952+   7  HPFS/NTFS
/dev/sda2               1         444     3566398+  12  Compaq diagnostics
/dev/sda3           16382       30401   112615650    5  Extended
/dev/sda5           16382       29826   107996931   83  Linux
/dev/sda6           29827       30401     4618656   82  Linux swap / Solaris

Partition table entries are not in disk order

and LSHW gives this disk info:

           *-disk
                description: ATA Disk
                product: ST3250824A
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.AA
                serial: 5ND5VBZJ
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=7029465b
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 0cec0e91-32ba-bd4d-8811-e86d9877c781
                   size: 122GiB
                   capacity: 122GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-06-19 23:56:26 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:1
                   description: Windows FAT volume
                   vendor: RECOVERY
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: FAT32
                   serial: 7a5f-2414
                   size: 3482MiB
                   capacity: 3482MiB
                   capabilities: primary boot fat initialized
                   configuration: FATs=2 filesystem=fat
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   size: 107GiB
                   capacity: 107GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      logical name: /dev/.static/dev
                      capacity: 102GiB
                      configuration: mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 4510MiB
                      capabilities: nofs


 
/dev/sda1 is what I need to access, I think it should be loaded with NTF-3G, rather than be in FSTAB. But I don't know enough about NTFS-3G or how that is auto-mounted.

I see that the state=dirty but I have booted and rebooted the windows partition w/o error, so I don't know how to proceed.

I appreciate any help.

---

### Post by mc4man on 2009-01-03
you may want to try booting into windows and running a chkdsk

---

### Post by deamon_knight on 2009-01-05
Thanks, chkdsk cleared the dirty flag, the relavant protion of LSPCI now:

              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 0cec0e91-32ba-bd4d-8811-e86d9877c781
                   size: 122GiB
                   capacity: 122GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-06-19 23:56:26 filesystem=ntfs state=clean

However, I'm still getting the same "invalid mount option" error. Where are mount options for NTFS-3G loaded from?

---

### Post by deamon_knight on 2009-01-06
Well, I fixed it, but I'm not sure if this is a good fix or not. Per NTFS-3G website, I added 
"/dev/sda1 /media/windows ntfs-3g defaults 0 0"

to my /etc/fstab

and it looks like its working. Any possible side effects of going this route? Also, its just a matter of looks, but the partition is mount in places and on my desktop as 131GB Media. I'd prefer it to be labeled "Windows Partition". Any suggestions on how to do that?

Thanks

---

### Post by mc4man on 2009-01-06
You can change the volume label (displayed name) in either linux or windows.

For linux install ntfsprogs, unmount the drive, and as such. You must reboot to see change

```
sudo umount /dev/sda1
sudo ntfslabel /dev/sda1 Windows_Partition     [COLOR="Blue"]<- no space _[/COLOR]
sudo ntfslabel /dev/sda1   [COLOR="Blue"]<- to check new label[/COLOR]

```
Reboot

If you want Windows Partition as the label do it in windows ( spaces are allowed

control panel -> administrative tools -> computer management -> disc management. Right click on the partition -> properties and you can enter a new volume label there.

---

### Post by deamon_knight on 2009-01-06
Thanks MC4Man, I'll try that. That leads me to another question. In windows if I have a USB Stick drive I can rename it something like "DEAMONDISK" and it will also be named this when I read it in linux. How can I do this within linux?

---

### Post by mc4man on 2009-01-06
> In windows if I have a USB Stick drive I can rename it something like "DEAMONDISK" and it will also be named this when I read it in linux. How can I do this within linux?

Very easy, see this

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

The only ones that are a little tricky are vfat (fat16,fat32

read the instructions carefully and there's no problem

---

### Post by deamon_knight on 2009-01-06
Thanks again mc4man. I haven't had a chance to test this but my only remaining concern here is that removable NTFS devices won't automount correctly. I'll have to get one and find out.

---

### Post by deamon_knight on 2009-01-08
Well, I'm not really sure what happened, but other removable NTFS drives automount normally. Problem solved!

---

