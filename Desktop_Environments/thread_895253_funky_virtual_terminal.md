---
title: "funky virtual terminal"
date: 2008-08-20
forum: Desktop Environments
---

### Post by radtek on 2008-08-20
When I try to open a virtual terminal all I get is a corrupted screen; and when I f7 to return there is a corruption over part of my desktop that corrects itself after a few seconds.

What could this be?

---

### Post by prshah on 2008-08-20
> **radtek said:**
> When I try to open a virtual terminal all I get is a corrupted screen; and when I f7 to return there is a corruption over part of my desktop that corrects itself after a few seconds.


In your "corrupted" screen, blind-type the below command and see if the terminal recovers:```
reset
``` Don't worry, this simply resets the terminals display, it does not reset the computer.

---

### Post by pauper on 2008-08-20
It's likely that text console is not set up properly.

Try:
```
sudo modprobe fbcon
sudo modprobe vesafb
```

Or any other then "vesafb" chipset-specific driver from
/lib/modules/`uname -r`/kernel/drivers/video directory.

[http://www.mjmwired.net/kernel/Documentation/fb/fbcon.txt](http://www.mjmwired.net/kernel/Documentation/fb/fbcon.txt)

---

### Post by radtek on 2008-08-21
Tried them both but no worky...!

This is a fresh clean install too.

---

### Post by radtek on 2008-09-01
Interestingly enough I'm still experiencing this problem *even* after several clean installs (for other reasons I assure you) and I'm beginning to suspect it is a hardware degradation issue. Maybe.

Still if anyone has an idea I'd appreciate it.

---

