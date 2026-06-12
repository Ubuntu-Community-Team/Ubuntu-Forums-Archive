---
title: "AMD 64 bit processors"
date: 2008-12-30
forum: Full Circle Magazine
---

### Post by ellis rowell on 2008-12-30
I use an Acer Aspire 5101 Laptop with an AMD Turion64 processor. I have successfully installed Ubuntu v8.10/64, everything works fine including the Wifi. The exception is that Adobe Reader doesn't seem to have a 64 bit version available and the 32 bit version doesn't work on the 64 bit processor (says it's the wrong architecture), But at least we have Evince to take its place.

---

### Post by jpkotta on 2008-12-30
If you have a .deb, use dpkg with force-arch:
```
sudo dpkg -i --force-architecture foo.deb
```

---

### Post by ellis rowell on 2009-01-05
Update: I have overcome the problem by using Evince, I also found that with Ubuntu v8.10/64 KompoZer was quitting when using the drop down menu's with a mouse. My way out of this problem was to install Mozilla SeaMonkey instead of Firefox, Thunderbird and KompoZer. All is working well now.

---

