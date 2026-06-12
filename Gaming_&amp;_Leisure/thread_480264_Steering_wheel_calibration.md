---
title: "Steering wheel calibration"
date: 2007-06-21
forum: Gaming &amp; Leisure
---

### Post by samjh on 2007-06-21
I'm using a Logitech vibration feedback wheel (Nascar/F1 depending on region), and have difficulty with eliminating steering "deadzone".

In Windows, the wheel works fine, but in Ubuntu there is always a deadzone around the centre, around 20 degrees in each direction.  This occurs in both LFS (under Wine) and TORCS, so it is not application specific.  I've tried removing the deadzone within the programs themselves, but to no effect.

I've read somewhere that the Linux kernel has a deadzone hard-coded into it.  Is that true?  If it isn't true, how do I calibrate the wheel to reduce or remove the deadzone?

---

### Post by TomMK on 2007-12-29
I have this problem too. Anyone found a fix? Thanks.

---

### Post by TomMK on 2008-01-04
I found a solution to this:

```
sudo apt-get install jscalibrator
```

Now I have a problem with LFS incorrectly detecting my wheel as a gamepad - probably bad drivers. :confused:

---

