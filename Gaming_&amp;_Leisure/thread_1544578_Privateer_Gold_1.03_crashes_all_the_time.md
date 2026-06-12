---
title: "Privateer Gold 1.03 crashes all the time"
date: 2010-08-02
forum: Gaming &amp; Leisure
---

### Post by [censored] on 2010-08-02
Hi. 

I'm using Lucid, on a 2006 vintage intel imac, with a Radeon ATI Mobility X1600. Open source ATI drivers.

The problem is that Privateer Gold 1.03 keeps crashing with this message:

> drmRadeonCmdBuffer: -12. Kernel failed to parse or rejected command stream. See dmesg for more info.

dmesg yields this:


```
[ 2220.681794] QNX4 filesystem 0.2.3 registered.
[ 2220.759352] Btrfs loaded
[ 2885.188310] [drm:radeon_cs_ioctl] *ERROR* Failed to parse relocation -12!
[ 4347.717059] [drm:radeon_cs_ioctl] *ERROR* Failed to parse relocation -12!
```

Does anybody understand this problem? Is there a solution to it, or workaround?

---

### Post by [censored] on 2010-08-03
Discovered that downgrading to kernel 2.6.31-11-rt  seems to solve the problems. So unless anybody can see any reason why doing that is a bad idea, I shall mark this thread SOLVED.

---

