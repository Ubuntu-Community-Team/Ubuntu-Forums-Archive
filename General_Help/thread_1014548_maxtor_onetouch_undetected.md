---
title: "maxtor onetouch undetected"
date: 2008-12-17
forum: General Help
---

### Post by albino.hernandez on 2008-12-17
this external disk powers on when plugged to the usb port, twice it worked well but after a few updates and new applications I downloaded and installed, it is not mounted no matter what.
this is what I get:

$ sudo lshw -C disk
sudo: unable to resolve host ubuntu
  *-disk:0                
       description: ATA Disk
       product: Maxtor 92049U6
       vendor: Maxtor
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: RA53
       serial: H602XP8C
       size: 19GiB (20GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=9d099d09
  *-cdrom
       description: DVD reader
       product: DVD-ROM GD-5000
       vendor: HITACHI
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 0212
       capabilities: removable audio dvd
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
  *-disk:1
       description: SCSI Disk
       product: ZIP 250
       vendor: IOMEGA
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/sdb
       version: 51.G
       capabilities: removable
       configuration: ansiversion=5
     *-medium
          physical id: 0
          logical name: /dev/sdb
  *-disk
       description: SCSI Disk
       product: OneTouch gvggmnfjf     
       vendor: Maxtor
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdc
       version: 0125
       serial: 2HAPRHXL
       size: 232GiB (250GB)
       configuration: ansiversion=4

the device is there, why is not mounted?

Thanks in advance for your help 
AHB

---

### Post by Polygon on 2008-12-18
if the device is there, but not mounted, maybe try repairing the disk by opening gparted, selecting the correct disk, and somewhere in the options is a option to 'check/repair partiton', maybe try running that

if that doesn't work, maybe try manually mounting it?

sudo mkdir /media/DISKNAMEHERE
sudo mount -t FILESYSTEM_TYPE_HERE /dev/sd(x) /media/DISKNAMEHERE

replacing the commands with the correct entries of course.

---

