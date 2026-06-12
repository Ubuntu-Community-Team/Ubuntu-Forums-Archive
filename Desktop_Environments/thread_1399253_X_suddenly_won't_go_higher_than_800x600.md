---
title: "X suddenly won't go higher than 800x600"
date: 2010-02-05
forum: Desktop Environments
---

### Post by beddo on 2010-02-05
Hi,
I'm running 9.10 and for some reason everything was working fine yesterday.
Today when I come to switch on I'm met with an 800x600 resolution that I can't make any bigger. Checking /var/log/messages I'm now getting this in the logs which didn't show up yesterday.
The system didn't do any updates yesterday so I'm at a loss as to what has broken.

```
Feb  5 08:42:02 beddo kernel: [   29.946732] i2c-adapter i2c-0: unable to read EDID block.
Feb  5 08:42:02 beddo kernel: [   29.946736] i915 0000:00:02.0: VGA-1: no EDID data
Feb  5 08:42:02 beddo kernel: [   30.063748] i2c-adapter i2c-0: unable to read EDID block.
Feb  5 08:42:02 beddo kernel: [   30.063752] i915 0000:00:02.0: VGA-1: no EDID data
Feb  5 08:42:02 beddo kernel: [   30.167381] i2c-adapter i2c-0: unable to read EDID block.
Feb  5 08:42:02 beddo kernel: [   30.167386] i915 0000:00:02.0: VGA-1: no EDID data
Feb  5 08:42:04 beddo kernel: [   32.450741] i2c-adapter i2c-0: unable to read EDID block.
Feb  5 08:42:04 beddo kernel: [   32.450746] i915 0000:00:02.0: VGA-1: no EDID data
Feb  5 08:43:50 beddo kernel: [  137.862726] i2c-adapter i2c-0: unable to read EDID block.
Feb  5 08:43:50 beddo kernel: [  137.862731] i915 0000:00:02.0: VGA-1: no EDID data
Feb  5 08:43:55 beddo kernel: [  143.000457] i2c-adapter i2c-0: unable to read EDID block.
Feb  5 08:43:55 beddo kernel: [  143.000462] i915 0000:00:02.0: VGA-1: no EDID data

```

---

### Post by beddo on 2010-02-05
Well here's me looking through dmesg, trawling through drivers and everything.

It turns out its really simple. My VGA cable had slipped a little so it was still connected but one end of it was loose. Plugged it back in, rebooted and now it works fine!

So anyone who suddenly has EDID issues - check your cables!

---

