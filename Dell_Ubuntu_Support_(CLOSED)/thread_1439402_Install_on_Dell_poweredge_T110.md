---
title: "Install on Dell poweredge T110"
date: 2010-03-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jfabrizio on 2010-03-26
I bought a server [Dell PowerEdge T110]("http://www.dell.com/us/en/enterprise/servers/poweredge-t110/pd.aspx?refid=poweredge-t110&cs=555&s=biz") chassis Tower with Suse Enterprise  pre-installed.

The server features are:
1 16X DVD+/-RW ROM Drive SATA with SATA Cable for Win2K8 R2
1 iDRAC6  Embedded BMC
1 8GB di memoria (4x2GB UDIMM dual rank) 1.066MHz
2  500GB SATA 7.200rpm 3,5" disco rigido cablato
1 C17 cablato *** R1  per SAS 6iR/PERC H200, esattamente 2 unità  SAS/SATA cablate
1 PERC  H200 controller RAID
1 Processore Intel Xeon X3430 (2,4GHz, cache  8MB, Turbo)
1 Keyboard : Italian (QWERTY) Dell Standard Quietkey USB  Keyboard Black
1 Dell Black 2 Button USB Scroll Optical Mouse

There is a RAID 1 with 2 disk of 500GB. 

I try to install ubuntu but the installation procedure is stopped on  "Detect disks"
> "No disk drive was detected. If you know the name of the driver  needed by your drive, you can select it from the list"Is it a problem of detection of raid controller?

[update..]

I try to run ubuntu-desktop from cd. Ubuntu starts correctly and I  launch GPARTED and I see these partitions:

- sda1 (fat32): 73MB
- sda2 (lvm2): 8 GB --> Inf: Logical volume Management is not  yet  supported
- sda3 (ext3):  213 MB
- sda4 (extended): 496 GB
    - sda5 (swap): 2 GB
    - sda6 (lvm2): 454 GB -->Inf: Logical volume Management is not   yet supported

Can Anyone help me?

Thanks.

---

### Post by jfabrizio on 2010-03-29
[updates]

I read these threads:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530361](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530361)

[http://ubuntuforums.org/showthread.php?t=1305472&highlight=mpt2sas](http://ubuntuforums.org/showthread.php?t=1305472&highlight=mpt2sas)

The problem is the mpt2sas module for the H200 controller raid detection.

Can anyone know how to find and integrate this module in ubuntu-server cd installer?

Thanks.

---

### Post by dromorok on 2010-12-14
I'm having the same problem

Have you got a workaround.

Thanks and regards

---

### Post by lpanebr on 2011-07-11
Did you find a solution?

Luciano

---

### Post by idlemind324 on 2011-07-13
This is a link for the components that have been certified to work on Ubuntu 10.04 and Ubuntu 11.04. I do not specifically see where it says H200 / Perc 6i but the SCSI controller listed may be the actual name for that component as far as the computer knows.

[http://www.ubuntu.com/certification/hardware/201003-5452/components]("http://www.ubuntu.com/certification/hardware/201003-5452/components")

If the device (Perc 6i or H200) actually cannot be seen we need to get that hardware recognized so you can actually copy data for the install as I'm sure you're thinking. To do this I would assume you need to provide a driver to the installer. I'm treading in water I haven't personally had to do but I did find a few ways to possibly accomplish this.

[https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)

&

[https://help.ubuntu.com/community/Installation/FromKnoppix](https://help.ubuntu.com/community/Installation/FromKnoppix)

I wish I had a T110 here to try this out on but sadly the only thing I have in that range is a 310 but that is at a customers site.

Good Luck.

---

