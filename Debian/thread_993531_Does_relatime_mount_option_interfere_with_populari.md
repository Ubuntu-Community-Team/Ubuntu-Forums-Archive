---
title: "Does relatime mount option interfere with popularity contest data?"
date: 2008-11-25
forum: Debian
---

### Post by stream303 on 2008-11-25
I like to participate in the data collection provided by Debian's popularity contest, which I allow during setup.

One thing I also like to do is force the filesystem not to write timestamps to files marked read-only by using a mount point option in /etc/fstab.

Formerly, I used to use *noatime* in my fstab, but that made the data submitted from my box useless for the popularity-contest tally package.

Like Fedora and now Ubuntu, *relatime* is another option, but currently is not enabled by default with Lenny-Testing.  I do it manually by reconfiguring my /etc/fstab.  Example:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda6       /               ext3    **relatime**,errors=remount-ro 0       1
/dev/sda7       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

I haven't been able to confirm if using *relatime*, in it's current Lenny-Testing incarnation, will interfere with providing accurate results to PopCon.  I know *noatime* does, but I just don't want to submit bad info if relatime isn't prime time yet. 

[http://popcon.debian.org/](http://popcon.debian.org/)

---

### Post by basenvironment on 2008-11-26
As far as I know relatime should be fine. My understanding is that relatime is now updating atime as well. At least something like that was discussed on the kernel list about a year ago.

btw, during install you can select mount options at the partitioning stage so no need to do change to relatime manually unless you wish to do so.

---

### Post by stream303 on 2008-11-26
Ah, nice to know about being able to choose mount options at partition time.  I'll have to look for it again, as I just installed Lenny on my AMD/64 desktop before reading this!  I'm blown away.

Up next is the laptop, so I'll look for the mount option when I do that one.

Thanks for the tip!

---

