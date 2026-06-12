---
title: "copy all files from one ntfs partition to another without changing datestamps"
date: 2009-02-20
forum: General Help
---

### Post by perhhk on 2009-02-20
I've tried doing this in gparted which uses ntfs clone, but I always get an error. I've run chkdsk /f but I still always get an error, partition magic does so to. 

So, is there any utility which will allow me to copy and paste all the files but keep their original datestamp on the new partition.

thanks, perhhk

---

### Post by tombott on 2009-02-20
Try using the cp command with the -p switch

For example:

```
cp -R -p -v /media/disk1/* /media/disk2
```

/media/disk1 being the source folder and /media/disk2 being the destination folder.
You'll need to change these to the mount points you are using. Let me know if you need helping in finding this information.

The switches above as follows:

-R - copy directories recursively
-p - Preserve attributes
-v - Verbose (Outputs to screen what is being copied)

Let us know how you get on.

---

### Post by perhhk on 2009-02-21
Thanks very much, it worked perfectly(dates and all).

I swapped the drive letters and it was like nothing had changed :D.

---

### Post by perhhk on 2009-02-24
:( I formatted the old drive and came to discover it didn't apply to subdirs :(

---

