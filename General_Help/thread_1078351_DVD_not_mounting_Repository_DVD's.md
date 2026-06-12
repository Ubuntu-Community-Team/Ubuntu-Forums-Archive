---
title: "DVD not mounting Repository DVD's"
date: 2009-02-23
forum: General Help
---

### Post by dohcdoh on 2009-02-23
I am running Ubuntu 6.10, and have since it was offered. It has been the perfect OS for me until . . .
I am limited to dialup, and eventhough I the software loaded that I need I wanted Repositories at hand for backup.

Problem: I have DVD repositories for Ubuntu 6.10 Edgy. Using " Add Cdrom" in Software Resources or in Synaptic the DVD disk in not recognized.

   (To add DVDs in Repository lists
      1. Settings -> Repositories -> Third Party
      2. Insert first DVD in drive and click Add Cdrom
      3. Name the added DVD
      4. repeat for other DVDs also)

The computer shows the CD and the DVD drive. Below: partial display of lshw -class disk.

  *-cdrom:0
       description: CD-R/CD-RW writer
       product: HL-DT-ST GCE-8160B
       physical id: 0
       bus info: ide@1.0
       logical name: /dev/hdc
       version: 2.01
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw
     *-disc
          physical id: 0
          logical name: /dev/hdc
  *-cdrom:1
       description: DVD reader
       product: SAMSUNG DVD-ROM SD-608
       physical id: 1
       bus info: ide@1.1
       logical name: /dev/hdd
       version: BT01
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio dvd
     *-disc
          physical id: 0
          logical name: /dev/hdd

I checked the bios setup. The DVD drive is setup similar to the CD drive. That is OK.

I can access the DVD disc with a file manager or the commandline. A CD data disk in the CD drive is mounted and opens the file manager autonatically. A CD data disk loaded in the DVD drive also is mounted and opens the file manager automatically. On both drives, Synaptic acknowledges the Repositories files on the Ubuntu CD Install disk. The DVD plays both sound and video DVD's.

Obvious question: Why does Synaptic "see" the DVD disk? What is the "fix?"

The Repository DVD's were purchased from a quality distributer. Could it be the disks? I have purchaased disks from the firm without problem.
Thanks

---

### Post by dohcdoh on 2009-03-08
This question is solved. I reinstalled with Ubuntu 8.10

---

