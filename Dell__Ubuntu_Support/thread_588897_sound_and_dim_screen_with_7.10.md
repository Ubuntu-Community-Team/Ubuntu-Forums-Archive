---
title: "sound and dim screen with 7.10"
date: 2007-10-23
forum: Dell  Ubuntu Support
---

### Post by malcolm07 on 2007-10-23
I upgraded to 7.10 and have two hardware problems on my Dell Inspiron 1420:

1. My sound has disappeared. Perhaps I overwrote a proprietary codex? Or something else?

2. In battery mode, my screen dims after 1 minute. I've changed the options in the power management area but it has made no difference. In battery mode, I'm constantly having to adjust the brightness back up to a useable level.

Any thoughts? Thanks!

---

### Post by Gen2ly on 2007-10-23
I set the dimmiing settings for the monitor/lcd in my xorg.conf.  This might just work.  In the server layout section severa values can be set:

```
# Monitor Poweroff
    Option  "BlankTime"    "5"     # Blank the screen in 5 min(Fake)
    Option  "StandbyTime"  "10"  # Turn off screen after     (DPMS)
    Option  "SuspendTime"  "20"  # Full suspend after 20 minutes
    Option  "OffTime"      "30"  # Turn off after half an hour
```

---

