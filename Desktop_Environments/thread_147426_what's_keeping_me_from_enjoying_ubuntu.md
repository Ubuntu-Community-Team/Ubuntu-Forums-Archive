---
title: "what's keeping me from enjoying ubuntu"
date: 2006-03-20
forum: Desktop Environments
---

### Post by oneiropolos on 2006-03-20
Hello guys! Ok here is the story:
some days ago i installed ubuntu on my pc (P4 3Ghz, 1 Gb ram, 2 hard drives 80 Gb's each). Installation completed. The only problem i faced was with the DHCP network configuration so i opted for "Do not configure the network at this time" or sth like that, but as far as i know i can configure it later anyway, isn't that right?

anyway after the installation i logged in and everything was fine. The following day, when i was starting the pc, the following message kept flashing on my screen:
"Buffer I/O error on device sda1, logical block 1773568 ata1:command 0x35 timeout, stat 0xd0 host_stat 0x61 ata1: translated ATA stat/err 0x35/00 to SCSI SK/ASC/ASCQ" So I restarted but: "Error 17" and ubuntu wouldn't start :(

I reinstalled ubuntu with no problems again (except for the DHCP issue) and came across the same problem when restarting my pc. From the message i may suppose that there is a problem with my first hard drive? should i try to install ubuntu on sdb1? what should i do?

Help plz!
Thanx in advance
A linux newbie

---

### Post by gnu2tux on 2006-03-20
hmm, are you sure that sda is your hard drive? Is it a SATA drive or an IDE drive?

If it's ide, it'll be on something like hda rather than sda. Are you sure you don't have anything connected like a flash drive or similar external media? Or perhaps you have a faulty CD writer or something like that?

My hard drive is sda, but that's because it's SATA RAID. 

>should i try to install ubuntu on sdb1? what should i do?

you could try it. I'd recommend if sda really is your hard drive, you should scan it for errors first, using either e2fsck or something low level like partitionmagics disk cheker to identify the problem better. Drive errors don't appear for no reason!

Regards

Al

---

### Post by ap9er on 2006-03-20
Sata drives are listed as sd* and IDE are listed as hd*.
So his drive is a SATA.

---

### Post by gnu2tux on 2006-03-21
But so are flash drives and scsi drives - so you may be wrong ap9er - that's why I'm checking.

the best way is to see the contents of /etc/fstab to see what is mounting.

---

