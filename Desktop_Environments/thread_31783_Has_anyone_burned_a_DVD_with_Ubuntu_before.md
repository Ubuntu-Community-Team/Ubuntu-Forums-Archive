---
title: "Has anyone burned a DVD with Ubuntu before?"
date: 2005-05-04
forum: Desktop Environments
---

### Post by Jonathan Drain on 2005-05-04
I can back things up to CD okay using the built-in CD Creator, but not DVDs; I haven't enough diskspace on my linux drive to write the disk image, and when I write the disk image to my FAT32 partition, CD Creator just kind hangs on me about 85% of the way through. Maybe it's stalling upon hitting four gig filesize?

Basically, I'm looking for some easy-to-use method in Linux of burning data to a DVD, which will function even though the only drive I have 4388MB free on is FAT32. Suggestions?

---

### Post by Jonathan Drain on 2005-05-04
Hm, I found this to work:

```
growisofs -Z /dev/dvd -R -J /path/to/dvd
```

Thanks!

---

### Post by rbprogrammer on 2006-06-02
is the built in CD "[COLOR="Red"]Creator[/COLOR]" you are talking about K3B? because that is what i use for backing up CDs and DVDs. if you didnt check that out yet, you should...

---

