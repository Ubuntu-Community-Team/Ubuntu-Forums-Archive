---
title: "Guild Wars Problems using Cedega"
date: 2006-08-05
forum: Gaming &amp; Leisure
---

### Post by robtotheb on 2006-08-05
When I try to install Guild Wars using Cedega 5.2 I get this Error:

```
X Error of failed request:  BadImplementation (server does not implement operation)
  Major opcode of failed request:  129 (MIT-SHM)
  Minor opcode of failed request:  5 (X_ShmCreatePixmap)
  Serial number of failed request:  3531
  Current serial number in output stream:  3532
X Error of failed request:  BadDrawable (invalid Pixmap or Window parameter)
  Major opcode of failed request:  55 (X_CreateGC)
  Resource id in failed request:  0x320034d
  Serial number of failed request:  3536
  Current serial number in output stream:  3539
Traceback (most recent call last):
  File "/usr/lib/transgaming_cedega/Point2Play_gui.py", line 2391, in monitor_cb    for i in self.monitor:
KeyboardInterrupt
```

No idea what it means, any ideas?

---

### Post by Upochapo on 2006-08-06
hi there!  I caught ur post.  I'm no expert and only been with ubuntu for 2 months but I caught the line about invalid pixmap.  I had a similar error and it had to do with the GW splash screen that loads up.  Apparently there are two different splash screens or at least one with an option missing in it.  Sorry, but it's been a while.  When does this error occur?  Are you able to get to the splash screen that says Install GW or Direct X?

If u tried installing it one time and the install process gets interrupted or cancelled, it has trouble calling up the splash screen again.  I will try to help as best I can from memory as this was a while ago.  But your problems sounds vaguely familiar to the one I had.  Take care.

Upo

---

