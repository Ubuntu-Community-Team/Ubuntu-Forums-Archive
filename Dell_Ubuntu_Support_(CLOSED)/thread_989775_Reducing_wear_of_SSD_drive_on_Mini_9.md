---
title: "Reducing wear of SSD drive on Mini 9"
date: 2008-11-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by yakker.yak on 2008-11-22
I noticed that the eeepc version of Ubuntu includes some settings intended to improve the lifetime of the SSD drive [1]:

"Flash drives are faster than regular hard drives, but their life time is reduced by the number of times it's written to. Ubuntu likes writing to the hard drive all the time: temporary files and just a little write here and there in between, to keep the drive alive. This behavior is not wanted by SSD owners though."

Does anyone know why the Dell Ubuntu doesn't make use of these SSD-optimized settings?

[1] [http://www.ubuntu-eee.com/wiki/index.php5?title=How_to:_make_the_fstab_changes](http://www.ubuntu-eee.com/wiki/index.php5?title=How_to:_make_the_fstab_changes)

---

### Post by rek075 on 2008-11-24
Not sure, but I'm definately interested in this.  Have you implemented these changes?  I noticed that the fstab on the mini 9 shows the ssd as using ext3, which they recommend against.  It's also quite bare.

---

### Post by snowpine on 2008-11-25
Probably because Dell feels their SSD will last as long as a typical mechanical HDD, even without any special tweaks.

---

