---
title: "No hard disks detected while installing Ubuntu GNU/Linux server 10.04 on Dell PowerEd"
date: 2010-08-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by EmreSevinc on 2010-08-17
I'm trying to install Ubuntu GNU/Linux server (10.04  LTS, 64-bit) on a Dell PowerEdge 2900 server hardware, and when it comes  to the disk and partition detection phase it says:

  "No disk drive was detected. If you know the name of the driver ..."
  
I switched to another tty and tried to see the output of lspci and in the output I have seen
  
"SCSI storage controller: LSI Logic / Symbios Logic SAS1068 PCI-X Fusion-MPT SAS (rev 01)"

  And then it presents a list of drivers, I have tried some of them but they did not work. 

  How can I proceed?

  Extra info:
  Dell server BIOS Revision 1.5.1

Dell SAS 5 Host Bus Adapter BIOS
MPTBIOS-6.12.02.00 (2006 12.22)
Copyright 2000-2006 LSI Logic Corp.

---

### Post by MGelbana on 2012-07-30
Anyone please ?
I'm in a similar situation. Headless Ubuntu server 12.04, Dell R710 server, 3 SAS drives and none of them were detected after I disabled the HW RAID.

---

