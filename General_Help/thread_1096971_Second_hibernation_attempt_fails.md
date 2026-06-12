---
title: "Second hibernation attempt fails"
date: 2009-03-15
forum: General Help
---

### Post by afeasfaerw23231233 on 2009-03-15
I have 1GB of RAM installed but the IGP occupies 128MB so only 896MB is available. I set the /swap as 956 and I thought that should be enough. 

It can hibernate for the first time but in the second time it fails and says ```
Can't hibernate: not enough free swap 
```

Here's my free -m ```

free -m
             total       used       free     shared    buffers     cached
Mem:           880        564        315          0          9        140
-/+ buffers/cache:        414        465
Swap:          956        394        562

```
Here's my grub/menu.lst
```
 
title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		25053297-13ad-4ad2-8e86-e4bb594c5f7d
kernel		/vmlinuz-2.6.27-11-generic root=UUID=24df0199-31f4-47b6-b604-94a521ddad60 ro   idle=mwait
initrd		/initrd.img-2.6.27-11-generic


```

How can I fix it? Thanks!

EDIT: I am using ubuntu 8.10 32-bit 2.6.27-11 i686

---

### Post by afeasfaerw23231233 on 2009-03-16
bump

---

### Post by afeasfaerw23231233 on 2009-03-17
bump

---

### Post by afeasfaerw23231233 on 2009-03-19
bump

---

### Post by afeasfaerw23231233 on 2009-03-21
bump

---

