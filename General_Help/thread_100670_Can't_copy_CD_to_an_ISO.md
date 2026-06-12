---
title: "Can't copy CD to an ISO"
date: 2005-12-08
forum: General Help
---

### Post by ceverett on 2005-12-08
Specifically,

dd if=/dev/cdrom1 of=file.iso bs=1024
dd: reading `/dev/cdrom1': Input/output error
0+0 records in
0+0 records out
0 bytes transferred in 0.035665 seconds (0 bytes/sec)

I get the same result if I use sudo or swap /dev/hdc for /dev/cdrom1 ...
what's going on here?

This also faild on my Ubuntu Pentium-M laptop, so it's not an AMD64 issue.

---

### Post by yoyoned on 2005-12-08
Why are you using dd?  use cdrecord

---

### Post by dtessier on 2005-12-08
[QUOTE=ceverett]Specifically,

dd if=/dev/cdrom1 of=file.iso bs=1024
dd: reading `/dev/cdrom1': Input/output error
0+0 records in
0+0 records out
0 bytes transferred in 0.035665 seconds (0 bytes/sec)

I get the same result if I use sudo or swap /dev/hdc for /dev/cdrom1 ...
what's going on here?

This also faild on my Ubuntu Pentium-M laptop, so it's not an AMD64 issue.[/QUOTE]

Are you trying to copy an audio CD? If so, dd will not work.

---

### Post by albinoloverats on 2005-12-08
Have you tried
```
cat /dev/cdrom> image.iso
```
from the terminal?

Just a thought ;)

---

### Post by tonysathre on 2005-12-08
gnomebaker is a good app for burning ISO images

---

### Post by kingsidy on 2005-12-08
use k3b. it is an excellent burning application for linux.

---

### Post by Bachstelze on 2005-12-08
use k3b if you're running Kubuntu (KDE) for Ubuntu (GNOME), use GnomeBaker instead.

---

