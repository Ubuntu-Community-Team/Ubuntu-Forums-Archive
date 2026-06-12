---
title: "mounted disk appear strrange on desktop"
date: 2008-05-17
forum: Desktop Environments
---

### Post by Azyx on 2008-05-17
Hi.
I have 4 hdd qand 3 are the same model. The disk popup on my desktop with the name 300.1 GB media,300.1 GB media,300.1 GB media, 120.0 GB Media. I can not change their name :(

My fstab look like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=b38f33f4-66e5-4fe4-bbef-00f88a494478 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda2 -- converted during upgrade to edgy
UUID=93ce9162-fb61-46d7-ac0c-58c29809cd84 /home ext3 defaults 0 2
# /dev/hdg1 -- converted during upgrade to edgy
UUID=a1d838c2-5b99-495e-a97e-bb63392f1978 /media/100GB_F ext3 defaults 0 2
# /dev/hde1 -- converted during upgrade to edgy
UUID=feb51e21-b316-4f18-b1d1-d161c3a646f7 /media/280GB_C reiserfs defaults 0 2
# /dev/hdf1 -- converted during upgrade to edgy
UUID=a598b288-df32-4404-8348-a47aa0fcd150 /media/280GB_D reiserfs defaults 0 2
# /dev/hdh2 -- converted during upgrade to edgy
UUID=1c7a4002-4a38-4e0d-9c1c-1b047ccb156c /media/280GB_E ext3 defaults 0 2
# /dev/hda3 -- converted during upgrade to edgy
UUID=f956f07f-9c3f-43d0-9d21-98ae673ef407 none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0

As you can see I have namned the disk from 280GB_C to 100GB_F so I can see any different between them. The problem is that 3 of the disk have get the same name from HARDY HEARON. I uppgrade from Dapper, cos no Ubuntu after Dapper except, his last had not abillity to read my disks on my ATA-card.

How can I change name on the media-disk that automatic get viewed on the desktop by Hardy-Heron and get the same name cos the have the same size. When i look on the disk, I see the right mane I have get them, but I want to se which disk it is BEFORE I open the disk!!

/Azyx

---

### Post by vanadium on 2008-05-17
Label the disk. How depends on the file system.

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

(applies equally well for fixed disks mounted under /media)

---

### Post by Azyx on 2008-05-18
> **vanadium said:**
> Label the disk. How depends on the file system.

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

(applies equally well for fixed disks mounted under /media)

I maybe have wrong, but is'nt partition-label for instance sda1? Those i don't want to change, cos I have those disks on a NFS-network.

i dont think it's the partition-label that showing up on the desktop. It's Hardys own name for the disk (for instance "300.1GB media". booth reiserfs and ext3-FS get the same name.

/cheers Azyx

---

### Post by Azyx on 2008-05-18
> **vanadium said:**
> Label the disk. How depends on the file system.

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

(applies equally well for fixed disks mounted under /media)


In the beguinning of the document you linked to It says:

"Devices that auto mount will be mounted in /media using their label as a mount point (name)."

I mount in FSTAB, is that the same as auto mount? In that case, before Hardy Heron the mount-point name appears on the desktop, or when I mounted the same disks over NFS, the did not appear at all, on the desk. 300.1GB media is NOT a mount point name.

---

### Post by Azyx on 2008-05-18
> **vanadium said:**
> Label the disk. How depends on the file system.

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

(applies equally well for fixed disks mounted under /media)


In the beguinning of the document you linked to It says:

"Devices that auto mount will be mounted in /media using their label as a mount point (name)."

I mount in FSTAB, is that the same as auto mount? In that case, before Hardy Heron the mount-point name appears on the desktop. I dont think 300.1GB media is a mount point name, but 

Anothe problem I have is when i upgraded Gutsy to Hardy is that i mount the same disk on my other machine over NFS-network, they did not appear at all, on the desktrop on Gutsy. Only where I tell them to appear in FSTAB.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=4c897399-fdee-47d0-a0a0-c564d5828f29 /               ext3    defaults,erro$
# /dev/hda3
UUID=9b3ac031-4a5b-4d67-ba35-bf3a7bd42f5e /home           ext3    defaults     $
# /dev/hda2
UUID=c3ee59f9-4a0c-41d5-bb48-2f6832403a0b none            swap    sw           $
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
#  NFS-mounting of DasBlack shade disks
10.1.1.2:/media/280GB_C /home/a/Desktop/DasBlack_NFS/280GB_C    nfs     rsize=3$
10.1.1.2:/media/280GB_D /home/a/Desktop/DasBlack_NFS/280GB_D    nfs     rsize=3$
10.1.1.2:/media/280GB_E /home/a/Desktop/DasBlack_NFS/280GB_E    nfs     rsize=3$
10.1.1.2:/media/100GB_F /home/a/Desktop/DasBlack_NFS/100GB_F    nfs     rsize=3$

Now the disks both mounts in /home/a/desktop/dasblack_NFS and as separate disks on my desktop, but here they have the mount point name '280GB_C', not some strange '300.1GB media'

/cheers Azyx

---

