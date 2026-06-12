---
title: "ManDVD not seeing my DVD drive"
date: 2009-03-19
forum: General Help
---

### Post by Szas on 2009-03-19
It works fine up until I get to the point where I try and burn my dvd to disc, then it kicks out and tells me it can't see my drive.  I think the drive is setup correctly.  When I put in a blank I get the shortcut on my desktop pointing to the blank disc.  Here is a screen shot of what it's doing
[http://www.ubuntu-pics.de/bild/11295/screenshot_030_qxBis6.png](http://www.ubuntu-pics.de/bild/11295/screenshot_030_qxBis6.png)

Any ideas?

---

### Post by Szas on 2009-03-19
If I change the location of my drive to /media/cdrom0 then Mandvd immediately pops up a "burning successful" but it does nothing.  
Here is another screenshot [http://www.ubuntu-pics.de/bild/11299/screenshot_033_FJDxhH.png](http://www.ubuntu-pics.de/bild/11299/screenshot_033_FJDxhH.png)

Here is the content of my fstab file

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=78370c45-819c-41f1-9e0e-637c6c74e5b7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=d1407a91-39cc-4d40-9267-855bc27e7757 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by Szas on 2009-03-20
Still no luck.  I can read CDs just fine and it LOOKS like everything is right but I still can't get it to burn anything to disc.

---

### Post by Szas on 2009-03-22
Anybody?  This problem is REALLY annoying.

---

### Post by Szas on 2009-03-23
No luck using Brasero either.  It looks like everything is correct, but the burn button stays greyed out [http://www.ubuntu-pics.de/bild/11452/screenshot_046_p4ft7l.png](http://www.ubuntu-pics.de/bild/11452/screenshot_046_p4ft7l.png)

---

### Post by Szas on 2009-03-27
Anybody?  This problem is really hamstringing me.  I ditched MS on all my main machines two weeks ago and basically did the "total immersion" thing to force myself to learn/adapt to linux.   So far everything is going good except for this one problem.

---

