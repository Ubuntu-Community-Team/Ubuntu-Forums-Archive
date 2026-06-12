---
title: "utility to show memory timings etc?"
date: 2008-12-10
forum: General Help
---

### Post by paulgj on 2008-12-10
Hello,

I was wondering if there is a utility that I can run that will show the memory information similar to how cpu-z shows it with speed, SPD info,latency timings etc?

I am running Hardy Heron 32-bit.

Thanks!

---

### Post by dcstar on 2008-12-10
> **paulgj said:**
> Hello,

I was wondering if there is a utility that I can run that will show the memory information similar to how cpu-z shows it with speed, SPD info,latency timings etc?

I am running Hardy Heron 32-bit.

Thanks!

```
sudo lshw
```

---

### Post by paulgj on 2008-12-10
Thanks! that's a lot of information although it doesn't give a huge amount of specific detail on the memory itself. (doesn't show the SPD info or the CAS timings).  Is there another option for that?

Thanks!

---

### Post by prshah on 2008-12-10
> **paulgj said:**
> (doesn't show the SPD info or the CAS timings).  Is there another option for that?

memtest will give you these details; it's available in the bootup GRUB menu or off a live CD.

---

### Post by paulgj on 2008-12-10
Thanks prshah, i'll give that a try.

---

### Post by mulp on 2009-02-01
> **paulgj said:**
> Thanks! that's a lot of information although it doesn't give a huge amount of specific detail on the memory itself. (doesn't show the SPD info or the CAS timings).  Is there another option for that?


for cas latency, timing and other memory-stuff install the package i2c-tools and run:

sudo modprobe eeprom
decode-dimms

---

