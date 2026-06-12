---
title: "Data Recovery on NTFS through ubuntu"
date: 2009-06-09
forum: General Help
---

### Post by Neuster on 2009-06-09
Edit to better explain what happened.

I had an old Xp install, which was partitioned to use ALL of my hard drive.  I had ubuntu previously installed using WUBI.  I wanted the slightly better performance, so I backed up windows and whatnot, and cleared my HD and installed ubuntu.  It runs really well now, but I forgot to backup a folder which was outside my windows folders...

is there anyway to recover some files off the now repartitioned hard drive?

---

### Post by doas777 on 2009-06-09
> **Neuster said:**
> Edit to better explain what happened.

I had an old Xp install, which was partitioned to use ALL of my hard drive.  I had ubuntu previously installed using WUBI.  I wanted the slightly better performance, so I backed up windows and whatnot, and cleared my HD and installed ubuntu.  It runs really well now, but I forgot to backup a folder which was outside my windows folders...

is there anyway to recover some files off the now repartitioned hard drive?

if you mess up a partition, then TestDisk is the best bet for recovering it, but it sounds like it may already be too late. if you have already overwritten the area where the partition was, then you will have spuratic luck at best. also you will need another storage location with enough room to store the data you want to recover (the whole partition, not just the files.)

you can try photo-rec to see if you can recover the specific files. if you are lucky, they may be on a portion of the disk that has not yet been overwritten. 
check out ubuntu rescue remix. it has testdisk and photorec: [http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/)

more often than not, lost data remains that way, unless you notice it missing almost immediatly. 

good luck,

---

### Post by Neuster on 2009-06-09
I'm really hoping the installation didn't overwrite the files.  I'll try those.  Thanks.

---

### Post by Neuster on 2009-06-09
I'm pretty sure it's all gone.  Damn.  

Thanks!

---

