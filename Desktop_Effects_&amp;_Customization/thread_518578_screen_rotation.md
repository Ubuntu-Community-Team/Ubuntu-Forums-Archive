---
title: "screen rotation"
date: 2007-08-06
forum: Desktop Effects &amp; Customization
---

### Post by technician on 2007-08-06
Hi,
I'm new to Linux.
I have Radeon 1300 video card and a Viewsonic monitor. I would like to rotate it vertically.
Here's what I get when I tried to use xrandr:
michael@michael-desktop:~$ xrandr -o left
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  157 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  12
  Current serial number in output stream:  12

Any ideas on how to do that if at all possible?

Thank you.

---

### Post by os.getlogin on 2007-08-08
me too.  can anyone help?

Nate

---

### Post by scifi007 on 2007-11-15
I'm having the same problem.  This is one of those little things that's keeping me from switching away from windows entirely.

From what I've gathered, the main issue appears to be the lackluster support for ati cards.  How to fix it, though, I'm not sure.  I've seen lots of complaints and not a lot of solutions for this problem.

---

### Post by Zorael on 2007-11-15
I don't at all know if this is the case with ATI cards, but with Nvidia you need to add the RandRRotation option in the Screen section to get rotation support.

```
    Option         "RandRRotation" "on"
```

If this is something Nvidia-specific, feel free to ignore me.

---

