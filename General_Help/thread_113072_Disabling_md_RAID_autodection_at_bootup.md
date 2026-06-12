---
title: "Disabling md RAID autodection at bootup"
date: 2006-01-05
forum: General Help
---

### Post by The Belgain on 2006-01-05
Hi there,

Could someone tell me how to disable autodetection and starting of md raid devices at bootup in Ubuntu?  I'm wanting to use EVMS to manage my RAID devices, and EVMS and mdadm don't play well together.

I've tried deleting /etc/init.d/mdadm and /etc/init.d/mdadm-raid, as they seem to be the only init scripts which call mdadm.  I've rebooted, and the md devices still seem to get started at boot (dmesg shows them starting, and "cat /proc/mdstat" shows them as having been started).

How can I prevent md devices from being started by mdadm (or the kernel)?  EVMS is failing to activate my storage volumes, until I manually stop the arrays in mdadm ("mdadm --manage --stop <device>").  The partitions on these devices are set to Linux type, not Linux RAID autodetect by the way.

Also, why do the Ubuntu init scripts use mdadm to detect RAID arrays and then start EVMS?  The EVMS dev I asked about this said he thought this was not correct... (see [http://marc.theaimsgroup.com/?l=evms-devel&m=113649841228967&w=2](http://marc.theaimsgroup.com/?l=evms-devel&m=113649841228967&w=2))

Thanks.

---

### Post by The Belgain on 2006-01-09
Well, seeing as I've had no luck with this, I might just add a line to my init scripts to manually stop any arrays that have been autostarted (though this is hacky and not very neat).

I need to get this in before the EVMS volume activation stage in the bootup.  I can't find any scripts which start up EVMS though.  Where in the bootup process does EVMS volume activation happen?

---

### Post by cylon359 on 2006-01-09
To disable auto raid start, you probably have to change the partition types... It's most likely set to "linux raid auto" or something like that now... there should be a non-auto type in the fdisk partition listing.

---

### Post by The Belgain on 2006-01-09
Thanks for the suggestion, but I'd already made sure that none of my partitions were of type 0xfd (Linux RAID autodetect).  My partitions are of type 0x83 (Linux), and I'm still seeing this problem...

---

