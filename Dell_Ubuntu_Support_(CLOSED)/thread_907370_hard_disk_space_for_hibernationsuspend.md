---
title: "hard disk space for hibernation/suspend"
date: 2008-09-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by antiOST on 2008-09-01
Hi

I read a lot of guide for hibernation/suspend, theses guide tell how to configure this but lack an explanation on what I should be aware of regarding hard disk space.

If I have 4 GB of ram I should have same hard disk available for the content of ram to be written. But is this written to my swap partition or is it possible to define another partition og mounted folder?

Or shouldn't I worry at all and just configure..?

-Kim

---

### Post by forger on 2008-09-01
I think it depends on which applications you use for hibernation or suspend

---

### Post by antiOST on 2008-09-01
Hi

I just thought of using the built hibernation/suspend in Ubuntu Gutsy and tweak with help from guides if that doesn't work.

-Kim

---

### Post by unutbu on 2008-09-01
To hibernate you need a swap partition with at least as much space as your physical RAM.
The file /etc/initramfs-tools/conf.d/resume should look something like this:
```

RESUME=UUID=33b7e11e-5bdb-4e98-b626-671b1c4d18eb
```

where the long UUID string at the end should be the UUID of your swap partition.
You can find the UUID by running the command "blkid".

---

### Post by antiOST on 2008-09-01
Just what i needed to know. Thanks

-Kim

---

