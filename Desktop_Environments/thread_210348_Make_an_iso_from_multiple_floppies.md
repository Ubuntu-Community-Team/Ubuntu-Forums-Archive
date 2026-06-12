---
title: "Make an iso from multiple floppies"
date: 2006-07-06
forum: Desktop Environments
---

### Post by digimars on 2006-07-06
I'm trying to make an iso image from my 6 Windows 3.11 disks so that I can use it under VMWare Player (sounds silly, I know).  Can I use mkisofs to do this?  Or is there a more effecient way to do this?

---

### Post by mlind on 2006-07-06
you could try copying contents of all floppies to one temporary directory, then use
mkisofs
```

mkdir /tmp/test
cp -R /media/floppy/* /tmp/test  #for each floppy
mkisofs -o image.iso /tmp/test

```

---

### Post by digimars on 2006-07-06
would that also make it bootable?

---

### Post by mlind on 2006-07-06
[QUOTE=digimars]would that also make it bootable?[/QUOTE]

You need a boot image and for mkisofs if you want to make bootable cd. I think
package called **bootcd** could help you here. You also find many articles about
this using google and searching for "bootable mkisofs".

---

### Post by nab on 2006-07-07
these links aren't exactly what you are searching, but perhaps they help:
[http://www.mepislovers.org/modules/newbb/viewtopic.php?viewmode=flat&order=DESC&topic_id=16481&forum=10]("http://www.mepislovers.org/modules/newbb/viewtopic.php?viewmode=flat&order=DESC&topic_id=16481&forum=10")
[http://www.troubleshooters.com/linux/floppy_image_on_cd.htm]("http://www.troubleshooters.com/linux/floppy_image_on_cd.htm")

---

