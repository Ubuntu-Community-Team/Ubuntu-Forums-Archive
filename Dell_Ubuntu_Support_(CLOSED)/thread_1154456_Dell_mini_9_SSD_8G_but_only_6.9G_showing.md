---
title: "Dell mini_9 SSD 8G but only 6.9G showing"
date: 2009-05-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by EL-MINI 9 on 2009-05-09
Hi to all,

I am new to Linux, got my replacement 8G mini-9 due to defective battery. My original unit had 13G with free 8G under system monitor. The replacement has 6.9G with 3.9G free; Dell support recommended a BIOS check for the HDD it is 8G and said it is a software problem. Can someone please explain how to recover the difference? Thanks

---

### Post by jjacobs2 on 2009-05-10
Sounds like they shipped you the wrong hard drive the first time.  Hard drives always show up as being smaller than advertised in the OS.  7 gigabytes sounds about right for what they advertise as an 8 gigabyte drive.  Your original 13 gigabyte unit was probably a 16 gigabyte drive.

---

### Post by ugm6hr on 2009-05-10
> **jjacobs2 said:**
> 7 gigabytes sounds about right for what they advertise as an 8 gigabyte drive.

Indeed.

```
df -h
```

This shows my 8GB drive as 7.0GB too.

---

