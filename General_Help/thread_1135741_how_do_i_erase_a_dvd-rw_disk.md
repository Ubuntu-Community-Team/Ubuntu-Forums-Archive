---
title: "how do i erase a dvd-rw disk?"
date: 2009-04-24
forum: General Help
---

### Post by tanveerahmed2k8 on 2009-04-24
how do i erase a dvd-rw disk?
i burnt linux ubuntu 8.10 on a 4.3gb disc
 and when i put it in side , ubuntudoesnt say erase?
 how do i erase it?
and my disc doesnt seem to be recognised anymore??

---

### Post by SuperSonic4 on 2009-04-24
You can simply overwrite the disc with the next project to go on it :]

---

### Post by logos34 on 2009-04-24
If it's in restricted overwrite mode, you can simply overwrite.  Otherwise a fast blank/quick format is required before you can start anew in DAO sequential mode (growisofs command detects and does this automatically):

> Initially blank DVD-RW media is in Sequential mode. To format for Restricted Overwrite invoke 'dvd+rw-format /dev/scdN'. Once the media is formatted you don't have to reformat it to zap the content, it's more than enough to simply write over the existing data [with growisofs -Z ...]. Your unit might report some bogus media capacity (e.g. Pioneer DVR-x05 reports ~8GB or 178.5% of real capacity) right after initial format. It apparently just does so till you burn some data on it, so don't get fixated on this...

To change [back] to Sequential mode [or **to reuse the media in Sequential mode for a new dataset**] invoke '[COLOR="Red"]dvd+rw-format -blank /dev/scdN[/COLOR]'. Unfortunately specification requires lengthy, an hour per 1x media, -blank=full procedure applied before you can reuse the media for Incremental Sequential (but apparently not for Disk-at-once) recording. I really fail to understand why does it have to be that way, but that's the way it is. Period.

[http://fy.chalmers.se/~appro/linux/DVD+RW/-RW/](http://fy.chalmers.se/~appro/linux/DVD+RW/-RW/)


---

