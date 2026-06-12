---
title: "unable to mount local disk"
date: 2006-08-03
forum: Desktop Environments
---

### Post by Crypty on 2006-08-03
Hi, I'm trying to access my XP partition(NTFS) from ubuntu. When I double click the "local disk" in nautilus I get this message:

Unable to mount the selected volume.

error: device /dev/hda1 is not removable

error: could not execute pmount



Not sure what this means/why it's happening. Any help is appreciated.

---

### Post by Mithrilhall on 2006-08-03
What does your /etc/fstab look like?

---

### Post by Crypty on 2006-08-03
Here's my fstab

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by fragos on 2006-08-03
There is no fstab entry for /dev/hda1.  You can try using gparted to assign mount points without changing partition size or formating.

---

### Post by Crypty on 2006-08-03
Hmm, I looked around in gparted and couldn't find any way to set mount points.

---

### Post by h00s on 2006-08-03
Here you can find solution for your problem:
[http://tinyurl.com/sxbnf](http://tinyurl.com/sxbnf)

---

### Post by Crypty on 2006-08-03
> **h00s said:**
> Here you can find solution for your problem:
[http://tinyurl.com/sxbnf](http://tinyurl.com/sxbnf)

Got it. Thanks.:D

---

### Post by h00s on 2006-08-03
You're welcome :D

---

### Post by Crypty on 2006-08-07
Hmm it seems every time I restart,the windows folder disappears and I have to use the command again:
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

Is there a way to keep the partition mounted?

---

### Post by mod187 on 2006-08-09
> Hmm it seems every time I restart,the windows folder disappears and I have to use the command again:
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

Is there a way to keep the partition mounted?



I didn't see it at first, but if you scroll down a little in the link posted,
> Here you can find solution for your problem:
[http://tinyurl.com/sxbnf](http://tinyurl.com/sxbnf)
you will see how to mount drives on start-up.

---

