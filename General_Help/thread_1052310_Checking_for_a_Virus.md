---
title: "Checking for a Virus"
date: 2009-01-27
forum: General Help
---

### Post by the lemming on 2009-01-27
My mate has given me an external hard drive for me to put some data onto it via my Vista Box.

However I am worried that the drive may or may not have a virus on it which could be transferred onto my Vista box.

With this in mind is there any way that I can use my Ubuntu laptop to scan the external drive?

Cheers

---

### Post by Zip247 on 2009-01-27
if you have clamav installed, after ubuntu mounts the drive, from the command line run

```
clamscan -r /[COLOR="Red"]yourmountpoint[/COLOR]
```

change yourmountpoint to the mount point of the external drive

---

### Post by mb_webguy on 2009-01-27
A version of [AVG]("http://free.avg.com/download?prd=afl") is also available for Linux.

Note that neither ClamAV nor AVG for Linux will remove any infected files.  They're just scanners

---

