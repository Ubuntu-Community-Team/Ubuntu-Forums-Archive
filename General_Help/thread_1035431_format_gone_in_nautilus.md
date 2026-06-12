---
title: "format gone in nautilus?"
date: 2009-01-09
forum: General Help
---

### Post by rmausser on 2009-01-09
Maybe I am remembering incorrectly, but I remember there being a format as a right click option in Nautilus?

I am trying to format a mounted SD card. 

This is a fresh install of Ubuntu Studio 8.10 with the latest Kernel and updates. 

When I right click there is no "format" option. Not only for SD Card but any drives.

I loaded G Parted, and the SD card does not show up in there, so I can not format it that way either. 

How do you format devices in ubuntu?

---

### Post by sockrebel on 2009-01-09
I don't remember a format option in nautilus.

odd that it won't show up in GParted.

"mkfs" should work to format a partition.

```
mkfs -t ext3 /dev/sdX1
```

you can replace "ext3" with another file system type

and /dev/sdX1 is the path to your SD card.  make sure not to format something else!

---

### Post by rmausser on 2009-01-11
gracias

---

