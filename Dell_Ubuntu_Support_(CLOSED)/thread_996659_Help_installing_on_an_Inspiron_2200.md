---
title: "Help installing on an Inspiron 2200"
date: 2008-11-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by DemianTau on 2008-11-29
So, I downloaded Ubuntu because a friend recommended it to me. I set aside a 10GB Partition on my Hard Drive, and everything. I burned the correct image (not the alternate). Now, I boot up to the ubuntu prompt. I go to install, and it asks how I want to install it. When I select any option, it gives the following-

```
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
Error 15: File not found
Press any key to continue...
```

Any ideas so I can get this installed?

---

### Post by falcon61102 on 2008-11-29
When you boot up to the Ubuntu Menu, try selecting Check CD and let it run the integrity check.  Between the download and burn it may have been corrupted.

---

### Post by DemianTau on 2008-11-29
Uh, no progress bar or anything, it just sits there reading the disk.
The Hash checks out fine, and it runs the installer *in*windows, just not during boot.

---

### Post by falcon61102 on 2008-11-29
Sounds like you might have a bad disc.  Check the MD5 Hash of the .iso that you downloaded and if it's correct then file is good.  Then try burning it again and burn it at 1x.  Also, make sure you use a CD-R as CD-RWs are know to cause problems as well.

---

### Post by DemianTau on 2008-11-29
Alright, trying that now.

---

