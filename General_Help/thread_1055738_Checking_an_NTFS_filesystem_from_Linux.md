---
title: "Checking an NTFS filesystem from Linux"
date: 2009-01-31
forum: General Help
---

### Post by bilijoe on 2009-01-31
I have done several searches and can't seem to find any definitive answer regarding checking / fixing NTFS filesystems from Linux. There were a couple of posts that gave an "answer" but the procedure they described did not work for me. Maybe there is no way to check NTFS from Linux. If not, I'd really appreciate it if knowledgaqble person would just say that, outright, so I couold quit messing around trying to do something that's not supported.

---

### Post by mb_webguy on 2009-01-31
Install the package "ntfsprogs", then use the command "sudo ntfsfix /dev/xxxn" to scan an ntfs filesystem, where xxxn is the device to scan (such as sda1)

---

### Post by jrusso2 on 2009-01-31
I personally would not do it from Linux except as a last resort.  I would run it off a CD before I did that.

[http://kb.wisc.edu/helpdesk/page.php?id=5097](http://kb.wisc.edu/helpdesk/page.php?id=5097)

---

### Post by shane2peru on 2010-02-04
I did this on an image I took from a dying/dead hdd.  I made a backup copy of the image first then gave this a try, seemed to work like a charm.  I then mounted it with:```
sudo mount ntfs-3g location/image /mount/point
``` and it worked like a charm!  I was very impressed, and the fellow I recovered the data for was very thankful!

Shane

---

