---
title: "lubuntu and usb with persistence &gt; 4GB"
date: 2011-10-28
forum: Desktop Environments
---

### Post by mrmedia on 2011-10-28
lubuntu 11.10 and USB.

Success but after a bit of a juggle - re: installing to usb and increasing casper size.

Normally, is mount and write image to usb with unetbootin, with a small persistence setting. Use Gparted to reduce partition and create a new partition with ext2 labelled 'casper-rw' - use any size.
Then login and delete /cdrom/casper-rw and reboot. 

But Oneiric has issues and will not work until apt-get update,  apt-get dist-update ,apt-get upgrade. It fails to see new casper-rw partition.

So work around is ......  install to usb, login and run the apt-gets first.  Disk space is still small. Then go back to adding new partition. Then can log back in and the new partition is now mounted and is okay to delete casper-rw file and reboot.

It seems that the decision to go post beta for Oneiric was a bit premature. 
The command df will NOT show the 2nd partition and the persistence entry , as would be seen from linuxmint or ubuntu - but the /cow files size will be increased. Also gparted will show an error for 2nd partition in lubuntu.

But at least it works - great more than 4GB.

---

