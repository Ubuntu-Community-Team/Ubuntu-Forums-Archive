---
title: "Failed to shutdown LIVE CD session"
date: 2010-11-03
forum: Desktop Environments
---

### Post by 2009tester on 2010-11-03
I tested 10.10 LIVE CD Gnome version.

I did some disk operations on NTFS and FAT volumes.
It worked well.
When I wanted to shutdown from the right upper corner icon,
I got a black screen saying:
(process:272) GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)

it does not take any keyboard, incl cont+alt+del

may it be a bug?

---

### Post by ocboy949 on 2010-11-03
This happened to me the first time around and I concluded that the disc I was using had errors. So I burned a new one at 4x instead of 24x and haven't seen that error since.

---

### Post by 2009tester on 2010-11-03
Actually, I have used USB for live session.
I will check md5 of my ISO file.

I tried same session without any disk operation.
and shut down session.
I had below message repeating itself ENDLESSLY !!
It does not take any keyboard input.
==============================
[180.123456] serial 18250: too much work for irq16
+++++++++++++++++++++++++++++++
initial numbersin [] keep increasing at each line, but remainder of line is the same.

---

