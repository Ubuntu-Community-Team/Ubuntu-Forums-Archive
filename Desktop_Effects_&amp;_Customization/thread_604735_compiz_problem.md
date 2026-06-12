---
title: "compiz problem"
date: 2007-11-06
forum: Desktop Effects &amp; Customization
---

### Post by killerwhale65 on 2007-11-06
hi,

When i start compiz by typing compiz in the terminal, i have no titlebars anymore. Furthermore, when i start a new application, it does not appear anymore in the taskbar. Also i cant type anymore in the terminal.

This is the output from compiz:
> Checking for Xgl: not present.
Detected PCI ID for VGA: 01:00.0 0300: 10de:00f2 (rev a2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1920x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present.
Checking for FBConfig: present.
Checking for Xgl: not present.
Starting emerald
Segmentation fault (core dumped)
exec: 378: /usr/bin/metacity: not found


It used to work, but i did not have my monitor setup correct (i have 2  screens). So i have changed some things in the XORG file, and now my monitor setup is OK but compiz does not work.

What should i do?

thanks!

Matt

---

### Post by Happy_Man on 2007-11-06
Compiz, X, and dual monitors: not a good combo. So you kinda have to choose AFAIK. Do you want Compiz more, or dual monitors more?

---

### Post by killerwhale65 on 2007-11-07
Damn, are you absolutely sure compiz fusion does not work on dual monitors?

---

### Post by Happy_Man on 2007-11-07
It could, depending on whether Compiz loves you or not. :p

But seriously, there are really bad problems associated with this. My best bet (and the easier way out) is to just choose.

---

