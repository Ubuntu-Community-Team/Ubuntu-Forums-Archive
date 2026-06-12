---
title: "Unable to mount a blank DVD-R (Jaunty)"
date: 2009-06-05
forum: General Help
---

### Post by Kayden on 2009-06-05
So I'm planning to install Fedora 10 on another machine in the house, and have just finished downloading the respective iso. Every time I insert a blank DVD, however, Xubuntu fails to mount it automatically, although it mounts my Windows install DVD as well as my Xubuntu LiveCD flawlessly.

I then took the initiative of trying to mount it myself by using:
```
sudo mount /media/cdrom0
```
But that just gives me:
```
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
I've tried each of these suggestions, but to no avail. Maybe the message is correct, but I personally don't understand how a plain blank DVD-R could have any of these things wrong with it. Any help or suggestions would be **very** appreciated.

And again, for clarification, I'm using Xubuntu 9.04 32-bit.

---

### Post by sdennie on 2009-06-05
You can't really mount a blank CD because mounting assumes some sort of filesystem (which a blank CD does not have).  In nautilus, you should be able to right click on an .iso file and have the option to write it to disk.  The blank CD should be found and everything should work fine.

---

### Post by Kayden on 2009-06-05
> **sdennie said:**
> You can't really mount a blank CD because mounting assumes some sort of filesystem (which a blank CD does not have).  In nautilus, you should be able to right click on an .iso file and have the option to write it to disk.  The blank CD should be found and everything should work fine.
Thanks very much for the explanation. Shows how much I know, lol.

Yeah, I'd just figured out that I could just burn the image in the file manager. I feel so stupid now.

Thanks again. :popcorn:

---

