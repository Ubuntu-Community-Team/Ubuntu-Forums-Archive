---
title: "Application failed download"
date: 2010-05-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by brandonmiller21 on 2010-05-14
I was in the middle of downloading WINE for 10.04 on my laptop when it overheated and shut down....that obviously killed the download.  I let the system cool down then rebooted and attempted to download WINE again, but it tells me that the previous download failed and needs to be repaired before I can upgrade or re-install the software.  I decided I would mess with that later, but then when I tried to download Pidgin I got the same error......this was the first time I tried to download pidgin.  I have attached a screenshot of the error message I am receiving.

anything?

---

### Post by dv3500ea on 2010-05-14
Go to Applications -> Accessories -> Terminal
copy this:
```
sudo apt-get install -f
```
and paste it using ctrl-shift-v
press enter

---

### Post by brandonmiller21 on 2010-05-14
problem solved

:guitar:

---

### Post by brethren on 2010-05-14
i'd be more worried about my cpu overheating than a failed download. if you don't sort that problem your laptop will be toast.....literally

---

