---
title: "new dvd-rw drive issues..."
date: 2009-03-31
forum: General Help
---

### Post by rayj on 2009-03-31
Hello, everyone. I installed Xubuntu 8.10 on an old Dell computer, plugged in a new Sony DRU-V204A DVD-RW drive, and I'm having some issues with it.

It locks up whenever I put a burned DVD-R into it...specifically, an old DVD backup.

Here's the output of sudo lshw -C disk:

*-cdrom
       description: DVD-RAM writer
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       capabilities: audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: status=ready

It seems odd that it would see the drive as a SCSI, although it also sees the hard drive as SCSI, with no issues thus far.

I've tried setting the region for it with regionset, to no avail. Any ideas where to start looking?

Thanks in advance...

---

### Post by rayj on 2009-04-01
Anyone have any ideas? I'm starting to think that it might be the SCSI issue...

---

