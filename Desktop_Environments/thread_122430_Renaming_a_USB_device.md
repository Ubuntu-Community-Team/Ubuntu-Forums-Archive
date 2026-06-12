---
title: "Renaming a USB device?"
date: 2006-01-27
forum: Desktop Environments
---

### Post by siorai on 2006-01-27
I'm wondering if it's possible to rename a USB device that isn't always attached. I've been using my Playstation Portable for months now and it has always come up as "PSP" when I connect it. The other night, in an attempt to fix a minor issue with the PSP, I reformatted the memory stick. Now the PSP comes up as "465.5MB Removable Drive." Is it possible to have Ubuntu recognize it as "PSP" again?

---

### Post by awi on 2006-01-27
You need [COLOR="DarkGreen"]mlabel,[/COLOR] from [COLOR="DarkGreen"]mtools[/COLOR] package, and map your device to a letter in 

```
/etc/mtools.conf
```

---

### Post by xurizaemon on 2006-01-27
I thought this would be REALLY HARD too. Took me a while to work out that I just had to plug it into my OSX laptop, get-info on the volume, and change its name. You could do the same in Windows I expect too ... I'm not sure what the Linux tool is to change the volume labels, but e2label looks like it could be it ... there may be separate commands for different filesystems though (eg this tool maybe works only for ext partitions, not HFS or FAT32).

[http://www.tldp.org/HOWTO/Partition/labels.html](http://www.tldp.org/HOWTO/Partition/labels.html)

---

### Post by piq on 2006-01-30
I renamed my usb memory stick in osx and then my computer couldn't find it. The problem was solved when I formated it on yet another computer. Now it says *998,0 MB löstagbar volym again*, which is a bit boring, but at least it works.

---

