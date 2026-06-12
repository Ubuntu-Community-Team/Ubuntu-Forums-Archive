---
title: "copy to CD"
date: 2009-03-17
forum: General Help
---

### Post by Franz1 on 2009-03-17
Hi all, I have a copy of Ubuntu 8.10 on a DVD, I want to make a cd so that I can install on an older laptop that just has a cd rom.
What files do I need to burn to the cd?
Thanks in advance, Franz1

---

### Post by AoA Linux on 2009-03-17
Easiest way would prob be to download the cd iso of Ubuntu off of [www.ubuntu.com](www.ubuntu.com) then burn that to a cd to make sure you have everything you need.

---

### Post by LegendofTom on 2009-03-17
If you have the iso, just burn that to a CD.  Using the DVD sounds a little harder.

---

### Post by Seiji338 on 2009-03-17
Is it the standard 700 MB .iso that you burned to the DVD? If so follow this

Insert the DVD

```
sudo umount /dev/scd0
dd if=/dev/scd0 of=~/ubuntu.iso
```

Now you can burn ubuntu.iso to CD.

---

### Post by Franz1 on 2009-03-18
Thanks for help people.
Franz1

---

