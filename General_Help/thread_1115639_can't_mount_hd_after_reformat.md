---
title: "can't mount hd after reformat"
date: 2009-04-04
forum: General Help
---

### Post by the2020 on 2009-04-04
I formated my second hd from ntfs to ext3. When I try 
sudo mount /dev/sdb1 it says that 
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Also theres a 31.49 gb limit on my 80gb harddrive. I had this limit prob in windows also. Is it jumper settings? or is it because I have it as a slave drive?

---

### Post by evilaim on 2009-04-04
Well, if you reboot, the drive should automount.  if not, then you have to manually mount it.  You're missing a few flags in your mounting command.

sudo mkdir /media/secondary
sudo mount /dev/sdb1 /media/secondary -t ext3

There are a lot of tutorials and walk throughs for automounting hard drives, just remember to put the file system in, that's the -t flag.

Hope this helps.

---

