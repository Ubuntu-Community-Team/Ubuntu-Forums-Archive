---
title: "Where is my network card?"
date: 2009-01-06
forum: General Help
---

### Post by GIFRATE on 2009-01-06
I was wondering:

if a partition on my hdd is represented as a file as /dev/sda1,

where is the file that represents my network adaptor (eth0) located?

---

### Post by abn91c on 2009-01-06
> **GIFRATE said:**
> I was wondering:

if a partition on my hdd is represented as a file as /dev/sda1,

where is the file that represents my network adaptor (eth0) located?
/etc/network/ interfaces

---

### Post by GIFRATE on 2009-01-07
Thank you for you reply, but this file seems to be just a description of the interfaces, and not the actual one.

---

### Post by khelben1979 on 2009-01-07
Why do you need to find this file?

If you run the [dmesg]("http://en.wikipedia.org/wiki/Dmesg") command from a console you can get relevant information about your computer hardware over there, including your networks card. Maybe this can be useful in this regard?

---

