---
title: "Poweredge 1400SC install problem"
date: 2007-12-06
forum: Dell  Ubuntu Support
---

### Post by clarks on 2007-12-06
I am trying to install 6.06.1 LTS to a Poweredge 1400SC.  It will boot to the screen where you select "Install to hard disk", Install a LAMP server", etc.
When I select either to hard disk or LAMP, I get the following error after the kernel is uncompressed:

17179591.032000] i2o: iop0: could not activate controller

What's going on?  I can boot from a regular Ubuntu 6.06 livecd and everything works fine.  I have not tried to install from it yet as I really want to run the server edition.

Thanks in advance for any help!


***FOLLOWUP***
I have booted the server with the live cd and think i may have found the problem.  I started the Gnome Partition Manager and it does not recognize or show the SCSI disks at all.  It recognizes the attached ATA drive which is only storage.  The SCSI host adapter is an Adaptec AIC-7899P U160/m.  I could not find it on any compatibility list.

Will I need to disconnect the SCSI drives and try to install to the IDE?  I really don't want to do this, but can.

---

