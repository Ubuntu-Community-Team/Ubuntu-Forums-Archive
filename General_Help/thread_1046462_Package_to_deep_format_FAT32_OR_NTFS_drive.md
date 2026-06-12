---
title: "Package to deep format FAT32 OR NTFS drive"
date: 2009-01-21
forum: General Help
---

### Post by ade234uk on 2009-01-21
I am looking to sell my External 320GB hard drive. I was wondering if there is a package in Ubuntu that allows me to deep format a FAT32/NTFS drive. 

I want to wipe it properly, so that they cannot dig up any of my old documents in the future.

---

### Post by Titan8990 on 2009-01-21
You can download shred in the Synaptic Package Manager prior to reformatting. It will take a long time.

Also, DD is an alternative.


sudo dd if=/dev/zero of=/dev/sdxx


Use both tools with caution.

---

### Post by Tomatz on 2009-01-21
Zeroing data still leaves it (forensically) recoverable. I suggest you use dban:

[http://www.dban.org/](http://www.dban.org/)

---

### Post by Slim Odds on 2009-01-21
> **Titan8990 said:**
> sudo dd if=/dev/zero of=/dev/sdxx

```
sudo dd if=/dev/random of=/dev/sdxx
```

would be even better (or both).

---

### Post by bgerlich on 2009-01-21
> **Tomatz said:**
> Zeroing data still leaves it (forensically) recoverable.

Opinions on the subject are divided. DD is good enough for anyone not afraid of some secret government technology (or anyone not working in a environment riddled with cargo-cult-like or paranoid regulations).

---

### Post by Tomatz on 2009-01-21
> **bgerlich said:**
> Opinions on the subject are divided. DD is good enough for anyone not afraid of some secret government technology (or anyone not working in a environment riddled with cargo-cult-like or paranoid regulations).

:lolflag:

True! I guess i am a bit paranoid when it comes to personal data but i suppose that is a good thing ;)

---

