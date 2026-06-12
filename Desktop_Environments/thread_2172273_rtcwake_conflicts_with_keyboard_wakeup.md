---
title: "rtcwake conflicts with keyboard wakeup"
date: 2013-09-04
forum: Desktop Environments
---

### Post by cybernetic12 on 2013-09-04
I used to be able to wake up from suspend via keyboard, using Ctrl-Esc.  That setting was done in the BIOS.

Then I wanted to use rtcwake to wake up by the internal clock.  At first it didn't work, but I found out that if I choose in the BIOS menu to use "OS" instead of "BIOS" for wakeup, then rtcwake will work.  But then I lose the BIOS options for keyboard wake up (or USB / network / etc).

Now the problem is that rtcwake works but keyboard wakeup no longer works.  (I have not tried all key combinations, but it seems not to work).

If I do:
```
cat/proc/acpi/wakeup 
```
I get
```
PS2K      S3    *enabled   pnp:00:03
```

I assume that if rtcwake works, then the Ubuntu OS has control over the hardware wakeup functions.  But I don't know how to enable keyboard wakeup, when the BIOS was delegated the management to OS.

What else can I try?

---

