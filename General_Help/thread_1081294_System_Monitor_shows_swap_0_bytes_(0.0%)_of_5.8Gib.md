---
title: "System Monitor shows swap 0 bytes (0.0%) of 5.8Gib. Is this normal in ubuntu?"
date: 2009-02-26
forum: General Help
---

### Post by TJX09 on 2009-02-26
I have 2Gib memory and System Monitor shows swap 0 bytes (0.0%) of 5.8Gib. Is this normal in ubuntu? If not then how do i change it so swap works.

---

### Post by justleen on 2009-02-26
This is quite normal. Most modern systems with quite a bit off ram don't swap a lot. 
```

leen@just-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2023       1250        773          0         34        701
-/+ buffers/cache:        513       1510
Swap:         4506          0       4506

```

If your systems does start swapping, do keep an eye on the load of your system..

---

### Post by mpsii on 2009-02-26
With 2GB of RAM and "normal" desktop usage (ie - web surfing, email, word docs), you should not see swap usage much, IF EVER.

However, if you do any slightly fancy antics in GIMP or Kvidemux, you may see some swapping. If you use a database (mysql, postgresql, oracle) you will almost definitely see swap usage increase.

---

