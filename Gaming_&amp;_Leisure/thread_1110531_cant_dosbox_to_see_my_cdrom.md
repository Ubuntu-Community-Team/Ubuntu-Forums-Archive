---
title: "cant dosbox to see my cdrom"
date: 2009-03-29
forum: Gaming &amp; Leisure
---

### Post by LinuxWan on 2009-03-29
I use the syntax "mount e /dev/cdrom -t -cdrom -usecd0 -iotl

and it says it mounts but when I cd to it and dir I get *.* not found.


any help? thanks.

---

### Post by grossaffe on 2009-03-30
> **LinuxWan said:**
> I use the syntax "mount e /dev/cdrom -t -cdrom -usecd0 -iotl

and it says it mounts but when I cd to it and dir I get *.* not found.


any help? thanks.

try this:
```
mount e /media/cdrom0 -t cdrom
```

---

