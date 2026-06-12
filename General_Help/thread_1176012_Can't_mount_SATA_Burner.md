---
title: "Can't mount SATA Burner"
date: 2009-06-01
forum: General Help
---

### Post by gus_zernial on 2009-06-01
I have an AMD Phenom system running Kubuntu Jaunty 9.04 with a custom 
2.6.28.9 kernel. The system has an LG GH22NS30 SATA CD/DVD R/W drive.
When I try to mount the drive I get 

%sudo mount -t iso9660 /dev/sr0 /media/cdrom0
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

The system seems to recognize the device - I can see it in /proc
and /var/log messages - but I'm not sure what more information to 
post. I believe the method of handling SATA burners changed between 2.4
and 2.6, but I'm not sure how to configure/compile for this device and/or what modules I need to have loaded in 2.6. Help appreciated.

---

