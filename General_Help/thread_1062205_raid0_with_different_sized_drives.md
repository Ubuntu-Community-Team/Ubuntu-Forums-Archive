---
title: "raid0 with different sized drives?"
date: 2009-02-06
forum: General Help
---

### Post by syssyphus on 2009-02-06
I was going to setup raid across 2 usb hard drives but they are different sizes, I am pretty certain linux allows using all of the space (so if one was 60gb, and the other was 100, the resulting raid 0 drive should be 160gb) can anyone confirm this and let me know why I or anyone would want to span when raid 0 will apparently stripe until only one drive has empty space?


thanks.

---

### Post by syssyphus on 2009-02-06
I found this in the man pages:

[http://manpages.ubuntu.com/manpages/jaunty/en/man4/md.4.html](http://manpages.ubuntu.com/manpages/jaunty/en/man4/md.4.html)

...
If devices in the array are not all the same size, then once the smallest  device  has  been  exhausted,  the  RAID0 driver starts collecting chunks into smaller stripes that only span the drives which still have remaining space.
...

So I guess there really is no reason to use linear.

Thoughts?

---

### Post by dcstar on 2009-02-07
> **syssyphus said:**
> I was going to setup raid across 2 usb hard drives but they are different sizes, I am pretty certain linux allows using all of the space (so if one was 60gb, and the other was 100, the resulting raid 0 drive should be 160gb) can anyone confirm this and let me know why I or anyone would want to span when raid 0 will apparently stripe until only one drive has empty space?


You do realise that if one of your RAID0 devices fails you lose all your data on both drives?

As far as I'm concerned, RAID0 is totally misleading labelling as there is no "Redundancy" whatsoever and it halves the potential reliability of your storage - I cannot understand why anyone who cares about their data would do that.

---

### Post by fjgaude on 2009-02-07
> **syssyphus said:**
> I was going to setup raid across 2 usb hard drives but they are different sizes, I am pretty certain linux allows using all of the space (so if one was 60gb, and the other was 100, the resulting raid 0 drive should be 160gb) can anyone confirm this and let me know why I or anyone would want to span when raid 0 will apparently stripe until only one drive has empty space?


thanks.

Well, raid0 is usually used for speed, quickness beyond that of one drive alone. It is not linear, but stripping over two or more drives for speed, high throughput. If you do this make sure you have backups of important data, for sooner or later one of the drives will fail and then all is lost, period.

With two unequal drives you only get twice the smaller one in storage capacity.

---

