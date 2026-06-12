---
title: "Dell Latitude D630 - (Integrated Intel Video) Dual Display"
date: 2007-11-10
forum: Dell  Ubuntu Support
---

### Post by nafetski on 2007-11-10
Hey everyone, 

I'm a web developer, but still relatively new to ubuntu/linux as an OS.  Made the switch about a week ago, and I'm loving it.

However, I have had a hell of a time getting dual displays working.  I looked at all of the dual display threads, but they seemed more geared towards ATI and Nvidia cards...unfortunately I'm on a laptop and am forced into using the intergrated intel card.

When I go to the screen and graphics dialog box, I only see my laptops monitor (plug and play 1152X864).  When I attach the external monitor (LCD 19" 1280X1024) it mirrors fine, but I have no option to span the display across both monitors.

While in Screen & Graphics dialog box, the option to choose a monitor as secondary is greyed out.  Anybody else have similar problems?

Thanks in advance!

---

### Post by nafetski on 2007-11-10
This is what I get from lspci | grep Graphics

```
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

```

Just in case that would be the first question someone would ask =D

---

### Post by theproc64 on 2007-11-27
I have the same problem with my dell latitude d620 except vga output doesn't even work at all.

---

### Post by sciurus on 2007-11-29
Try this thread for dual display with spanning.

[http://ubuntuforums.org/showthread.php?t=617934](http://ubuntuforums.org/showthread.php?t=617934)

---

