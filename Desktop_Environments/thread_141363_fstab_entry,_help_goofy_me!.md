---
title: "fstab entry, help goofy me!"
date: 2006-03-08
forum: Desktop Environments
---

### Post by orazios on 2006-03-08
Before editing my fstab I was wise enough to back up my original file. I wish I had been wise enough not to delete the back up before I really was pleased with all entries! 
Can, please, anyone give me the original, unaltered entry for floppy /dev/fd0 ?

---

### Post by Mustard on 2006-03-08
```
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by Stealth on 2006-03-08
```
/dev/fd0  	/media/floppy  	auto  	rw,noauto,user,sync  	0 0
```

Seems to be it according to [this...]("http://www.tuxfiles.org/linuxhelp/fstab.html")

---

### Post by orazios on 2006-03-08
Thanks a lot, booth replies were helpful. Stealth's reference to tuxfiles gave a chance to dig deeper into Linux which I certainly need!

---

