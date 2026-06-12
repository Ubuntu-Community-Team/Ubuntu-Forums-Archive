---
title: "Dell GX270 framebuffer resolution"
date: 2011-01-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kc8hr on 2011-01-29
I wonder if somebody here could help me.

I have a Dell GX270 running Ubuntu 10.10. Works fine, except for one quirk: When I switch to a virtual console (ctrl-F1 - F6), the screen resolution is 1600x1200--the font is too small to read!

I have tried posting to other forums [http://ubuntuforums.org/showthread.php?t=1468789&page=3]("http://ubuntuforums.org/showthread.php?t=1468789&page=3") for an answer, but the solutions suggested did not work. I have tried modifying /etc/default/grub and /etc/grub.d/00_header, but nothing works.

The machine is using the i915 driver, which works well in X. Dmesg reports the following:

```
dmesg | grep uvesafb                                                [    6.358691] uvesafb: Intel Corporation, Intel(r)865G Graphics Controller, Hardware Version 0.0, OEM: Intel(r)865G Graphics Chip Accelerated VGA BIOS, VBE v3.0
[    6.366297] uvesafb: VBIOS/hardware supports DDC2 transfers
[    6.563930] uvesafb: no monitor limits have been set, default refresh rate will be used
[    6.564090] uvesafb: scrolling: redraw
[    6.565926] uvesafb: request region 0x3c0-0x3e0 failed
[    6.566925] uvesafb: probe of uvesafb.0 failed with error -5
```

I cannot figure out what is wrong. Is Plymouth ignoring my attempts to change the framebuffer resolution, or is it KMS?

I have no clue. Can anybody help? I would like to be able to use my virtual consoles!

Thanks,
Tim

---

### Post by kc8hr on 2011-02-06
Yippee! I found the fix here: [http://lkml.indiana.edu/hypermail/li...1.2/02116.html]("http://lkml.indiana.edu/hypermail/li...1.2/02116.html") The magic words are:

```
GRUB_CMDLINE_LINUX="video=VGA-1:640x480"
```
in /etc/default/grub. I now have a set of usable virtual consoles.

Later--
Tim

---

