---
title: "poor HDD performance in GNOME"
date: 2006-09-14
forum: Desktop Environments
---

### Post by macovey on 2006-09-14
I have following results of hdparm -tT in GNOME

/dev/hda:
Timing cached reads:   1392 MB in  2.00 seconds = 695.76 MB/sec
Timing buffered disk reads:   28 MB in  3.82 seconds =   7.33 MB/sec

(extremely slow)

BUT

in text console or IceWM all these values increase 4-6 times -- and overall performance is faster in IceWM or text console.

What's the reason? Anybody knows?

---

### Post by macovey on 2006-09-15
Later I discovered that perfomance issue caused by polling for "removable devices" by hal, dbus etc.

How can I improve my HDD performance without loosing removable devices support? Any suggest?

Does anyone tryed ivman instead of gnome-volume-manager?

---

