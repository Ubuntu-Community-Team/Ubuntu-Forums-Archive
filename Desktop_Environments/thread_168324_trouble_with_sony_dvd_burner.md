---
title: "trouble with sony dvd burner"
date: 2006-04-30
forum: Desktop Environments
---

### Post by frootstripe on 2006-04-30
Hi, 
having trouble with my dvd player/burner - must confess I haven't used it much except for watching dvds. 

Anyway, I can't mount a cd or dvd  mount anymore, and I don't have any icons on my desktop for storage devices.

my /etc/fstab entry is as follows:

/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0


dmesg error is:

 Error: Not ready -- (Sense key=0x02)
[4294954.667000]   Incompatible medium installed -- (asc=0x30, ascq=0x00)
[4294954.667000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4294954.667000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4294954.707000] ATAPI device hdc:

I did have my computer knocked over the other day, so perhaps this is the problem?? I'm not sure this is the case, as the cd seems to spin around but I suppose it could be. Thanks in advance, in case I forget to thank you later.

---

### Post by TransitMan on 2006-05-01
If you knocked over your machine, you need to shut it down, open it up, and with the power cord disconnected from it, make sure that all the connectors to the drives are secure. Once you veify that all the connectors are secure, close the case up, power up and see what you got.:-k 

If you still get errors, then the drive has probably been killed, :twisted:  and you will need to replace it.

---

