---
title: "Failed to tiling"
date: 2011-03-24
forum: Desktop Environments
---

### Post by Kognit on 2011-03-24
Hi

After i have woke up my computer from suspend mode and tried to login i got this message from xserver:
```
(ee) intel(0) failed to set tiling on front buffer input/output error
```

I have Ubuntu 10.04 and have the newest kernel from natty repository for lucid. Currently i have 2.6.38.7 kernel but intel and mesa drivers are the old ones. Everything worked fine till today though i had some problems from time to time when my computer has logged off automatically.

When the tiling problem appeared i noticed this message from Xorg log file:
```
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(EE) intel(0): Failed to set tiling on front buffer: Input/output error
(II) intel(0): Tiled allocation successful.
```
I haven't noticed this error in previous Xorg log files.

What could be the problem?

EDIT: I have Ubuntu not Kubuntu. By mistake i wrote down KUBUNTU up there.

---

