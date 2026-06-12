---
title: "Inspiron 1525 - Compiz Fusion / 3d effects"
date: 2008-06-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by GenesisV2.0 on 2008-06-23
HI 

I recently got hold of the Inspiron with Ubuntu Pre installed and i cant run Compiz fusion, i heard something about the black listed X3100 integrated graphics card but i dont know how to fix it, can anyone help?

cheers

---

### Post by liquidfunk on 2008-06-23
Is it not possible to enable the drivers from the Restricted Drivers Manager?

```
System -> Administration -> Hardware Drivers
```

 Try there.

---

### Post by danbodoh on 2008-06-23
The X3100 driver (actually the 'intel' driver) is open source (not a restricted driver) and is no longer blacklisted for this device.  I have compiz working on my 1525, both on Ubuntu 7.10 and 8.04.  The xorg.conf should be real basic because the intel driver has all the right defaults.  You can see a (modified) version of the video portion my xorg.conf at [http://ubuntuforums.org/showthread.php?t=822606](http://ubuntuforums.org/showthread.php?t=822606).  Take out the PreferredMode stuff from that listing.

Dan Bodoh

---

### Post by karasuman on 2008-06-24
I couldn't get it working with 7.10, but when I upgraded to Hardy, no problem.

---

