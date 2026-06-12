---
title: "Unable to mount the cdrom in Ubantu Kernel"
date: 2007-10-25
forum: Development CD/DVD Image Testing
---

### Post by connectrajeev on 2007-10-25
Hi All,

I am using 2.6.20-15-generic ubantu  kernel along with my customize root file system. On this systems I am unable to mount my CD drive. If I say "mount /dev/scd0 /cdrom " I get an error syaing "mount: mounting /dev/scd0 on /cdrom/ failed: No such device or address" 

I can see that OS has identified my CD drive, if I do "cat /proc/scsi/scsi" it shows me

"Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: ST340015A        Rev: 3.01
  Type:   Direct-Access                    ANSI SCSI revision: 05
Host: scsi0 Channel: 00 Id: 01 Lun: 00
  Vendor: TSSTcorp Model: CDW/DVD SH-M522C Rev: TS07
  Type:   CD-ROM"

I don't know why I am not able to mount the CD drive, please help if someone is having idea about it. 

Thanks
Rajeev Bansal

---

### Post by kinematic on 2007-10-27
What mountpoint is actually assigned to it in fstab?

---

