---
title: "choppy?"
date: 2009-02-13
forum: General Help
---

### Post by Alec Sacul on 2009-02-13
im running ubuntu 7.10 gusty gibson and its really choppy. its on a thinkpad and its an old thinkpad.. is it  a space issue because it works fine its just  really choppy

---

### Post by glotz on 2009-02-13
What CPU does it have? How much RAM?

---

### Post by Alec Sacul on 2009-02-13
I don't know how can I figure it out

---

### Post by glotz on 2009-02-13
For example with```
head /proc/cpuinfo && head -n1 /proc/meminfo
```

---

### Post by Alec Sacul on 2009-02-14
i got this when i typed them in
i know its a thinkpad
MemTotal:       377596 kB
MemFree:          7356 kB
Buffers:         56528 kB
Cached:         106684 kB
SwapCached:      25324 kB
Active:         263388 kB
Inactive:        77108 kB
HighTotal:           0 kB
HighFree:            0 kB
LowTotal:       377596 kB

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 8
model name      : Pentium III (Coppermine)
stepping        : 10
cpu MHz         : 700.000
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no

---

### Post by glotz on 2009-02-14
So you've got a pentium 3 @ 700 MHz and 380 megs of RAM. That's a pretty old system all right, perhaps you could be better off with some lighter distro, like damn small linux or puppy. There's plenty of to choose between depending on your preferences.

---

### Post by Alec Sacul on 2009-02-15
alright thanks

---

