---
title: "How to add multimedia library to /etc/apt/source.list"
date: 2018-05-17
forum: Debian
---

### Post by phani999 on 2018-05-17
hi, 
I am new to Linux please direct me how to add a multimedia directory to /etc/apt/source.list because I am unable to install faac in Debian 8.10.

Thanks in advance

---

### Post by wildmanne39 on 2018-05-17
*Thread moved to **Debian for a more appropriate fit**.*

---

### Post by Tadaen_Sylvermane on 2018-05-17
[http://www.deb-multimedia.org/](http://www.deb-multimedia.org/) has instructions. I'd suggest caution though. many people use it just fine no troubles. but there are some reports of packages conflicting with debian stable packages and causing issues.

---

### Post by deadflowr on 2018-05-17
You need to add the contrib non-free entries to the source entries.
[https://wiki.debian.org/SourcesList]("https://wiki.debian.org/SourcesList")
faac is in the non-free repositories.

Then you need to run an apt-get update so the new repositories are found by your system.

---

### Post by phani999 on 2018-05-21
> **deadflowr said:**
> You need to add the contrib non-free entries to the source entries.
[https://wiki.debian.org/SourcesList](https://wiki.debian.org/SourcesList)
faac is in the non-free repositories.

Then you need to run an apt-get update so the new repositories are found by your system.

Thank you I got the answer

---

### Post by phani999 on 2018-05-21
> **Tadaen_Sylvermane said:**
> [http://www.deb-multimedia.org/](http://www.deb-multimedia.org/) has instructions. I'd suggest caution though. many people use it just fine no troubles. but there are some reports of packages conflicting with debian stable packages and causing issues.
Thank you

---

### Post by mörgæs on 2018-05-21
Good, please mark the thread solved.

---

