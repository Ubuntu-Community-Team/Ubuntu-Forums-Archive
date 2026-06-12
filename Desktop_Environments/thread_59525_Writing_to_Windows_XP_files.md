---
title: "Writing to Windows XP files"
date: 2005-08-24
forum: Desktop Environments
---

### Post by Marrea on 2005-08-24
One thing I noticed about Ubuntu is that during installation, unlike SuSE, it didn't automatically create an entry in /etc/fstab for my Windows partition.  I have therefore added 

/dev/hda1	/mnt/win	vfat	auto,user	0   0

as a last line, but find I can only read Windows files, not write to them.  How do I amend the line so I can write to Windows files?  You will see that my Windows is FAT32 rather than NTFS, so I assume there wouldn't be any problem writing to the files?

---

### Post by nad on 2005-08-24
Add the read/write option: /dev/hda1 /mnt/win vfat rw,auto,user 0 0

---

### Post by DREMA on 2005-08-24
Is there anyway to write in my win2 partition if it have a NTFS file system  ???

---

### Post by Chris Cromer on 2005-08-24
As far as I am aware no, you can't write to a NTFS partition.

---

### Post by Marrea on 2005-08-25
[QUOTE=nad]Add the read/write option: /dev/hda1 /mnt/win vfat rw,auto,user 0 0[/QUOTE]
 Many thanks.   I'll give that a try.

---

### Post by mchatel on 2005-08-25
I don't believe Ubuntu itself (or most other Linux distros) will support writing to NTFS file systems, at this time, however...

I have heard of a separate add-on utility called "Captive NTFS", which does support this.  You might want to check out the web-site link below, for more info, or try and get some feedback from others, who may have tried this tool.

[www.jankratochvil.net/project/captive](www.jankratochvil.net/project/captive)

---

