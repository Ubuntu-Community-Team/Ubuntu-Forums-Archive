---
title: "HOWTO: Run Enemy Territory with sound using OSS"
date: 2007-04-04
forum: Gaming &amp; Leisure
---

### Post by Gorthus on 2007-04-04
I did a ton of searching around, trying to get enemy territory to run with sound on Ubuntu 6.10.. I finally found out how, and it was really simple :P

Here's what I use to run the game:

```
env WINEPREFIX="/home/gorthus/.wine" wine "C:\PROG~FBU\WOLF~R3I\ET.exe" USE="oss"
```

All you do is add 'USE="oss"' to the end, and it will work... Simple, no?

---

### Post by AthlonMDK on 2007-04-04
Too bad it is only for the windows version as far as i can see.

Thnx anyway! every bit of extra info is always welcome!

---

### Post by Gorthus on 2007-04-04
Wait, there is a linux version?

Crap...

---

### Post by blanky on 2007-04-04
Haha wow

---

