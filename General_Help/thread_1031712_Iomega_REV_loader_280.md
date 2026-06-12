---
title: "Iomega REV loader 280"
date: 2009-01-05
forum: General Help
---

### Post by 4Ahau on 2009-01-05
Hello,

I am fairly new to Linux, and have installed Kubuntu 8.04 on my desktop and laptop, so far all is working great. I have been searching the forums, and not finding much information regarding the Iomega USB REV Loader 280. Kubuntu sees the device and mounts media when it is manually inserted. What I am looking for is a command line way to load and unload media from the different slots. 

The Iomega REV loader holds eight 35GB REV disks, and used similarly like an auto changer tape drive. 

In the windows world I would have used the following type of command ( or placed in a batch file to automate backups )

C:\"Program Files\Iomega\REV System Software"\ImDrvCLI.exe /Drive=E /ChangeMedia /Source=2 /Destination=E

This would load media in slot 2, and mount as drive E. 

Does anyone know of a similar way or options to do the same in Linux?

Dmesg shows

[ 2306.948737] scsi 8:0:0:0: CD-ROM            Iomega   RRD              22.B PQ: 0 ANSI: 0
[ 2306.956581] scsi 8:0:0:1: Medium Changer    Iomega   REV LOADER       038C PQ: 0 ANSI: 0
[ 2306.964279] sr1: scsi3-mmc drive: 125x/125x caddy
[ 2306.964387] sr 8:0:0:0: Attached scsi CD-ROM sr1
[ 2306.964451] sr 8:0:0:0: Attached scsi generic sg2 type 5
[ 2306.970895] ch0: reading element address assigment page failed!
[ 2306.970902] ch0: INITIALIZE ELEMENT STATUS, may take some time ...
[ 2306.972006] ch0: ... finished
[ 2306.972054] ch 8:0:0:1: Attached scsi changer ch0
[ 2306.972119] ch 8:0:0:1: Attached scsi generic sg3 type 8

Thanks in advance for any and all help.

---

