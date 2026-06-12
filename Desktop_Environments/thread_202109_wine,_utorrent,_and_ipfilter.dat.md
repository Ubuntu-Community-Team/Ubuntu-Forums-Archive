---
title: "wine, utorrent, and ipfilter.dat"
date: 2006-06-22
forum: Desktop Environments
---

### Post by thegnark on 2006-06-22
so, i have utorrent running perfectly under wine (i was a long-time user of utorrent in windows)

but, i can't quite figure out where i should put my ipfiter.dat blocklist for it. in windows it goes in %AppData%\utorrent (which is C:\documents and settings\username\application data\utorrent). i tried placing the file in the same directory as utorrent, without any luck

is there a username i can create the directroy structure for? is there somewhere else i should look to put this?

---

### Post by rai4shu2 on 2006-06-22
In Wine, Application Data is placed in the c:\windows\profiles\$USER\ folder.

---

### Post by thegnark on 2006-06-22
[quote=rai4shu2]In Wine, Application Data is placed in the c:\windows\profiles\$USER\ folder.[/quote]

perfect! worked like a charm

---

