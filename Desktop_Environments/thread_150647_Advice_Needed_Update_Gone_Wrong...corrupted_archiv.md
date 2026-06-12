---
title: "Advice Needed: Update Gone Wrong...corrupted archive"
date: 2006-03-26
forum: Desktop Environments
---

### Post by welders4linux on 2006-03-26
E: /var/cache/apt/archives/libc6_2.3.5-1ubuntu12.5.10.1_i386.deb: corrupted filesystem tarfile - corrupted package archive

This is the message I get after installing a number of updates.  I try and rerun update but it has obviously cached the said updates and tries to re-install them to no avail.

If this is indeed the case do I just go to the *E: /var/cache/apt/archives/ * and delete everything there...then run update again?

Thank you for your advice
Cheers

---

### Post by aysiu on 2006-03-26
You could always try: ```
sudo rm /var/cache/apt/archives/libc6_2.3.5-1ubuntu12.5.10.1_i386.deb
```

---

### Post by lupine_nickt on 2006-03-26
Or apt-get clean ?

xF,

...Nick

---

### Post by welders4linux on 2006-03-26
[QUOTE=aysiu]You could always try: ```
sudo rm /var/cache/apt/archives/libc6_2.3.5-1ubuntu12.5.10.1_i386.deb
```[/QUOTE]

This is the first trick I tried.
it worked like a charm.

Thank you all for your advice, this truly is a great learning arena:D

---

