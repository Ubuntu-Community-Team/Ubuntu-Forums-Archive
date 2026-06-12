---
title: "KDE window resizing makes desktop go unresponsive"
date: 2011-05-03
forum: Desktop Environments
---

### Post by BigErn on 2011-05-03
The title of the post says it all.  When in the KDE environment with desktop effects enabled, KDE will often "freeze" when resizing a window, especially, if there is content such as other windows behind the window being resized.  It's actually not truly frozen, but the whole KDE becomes unresponsive and never recovers. (The mouse pointer can sometimes still be moved)  The xorg process at this point eats 99% of the cpu.

I am using an Nvidia gtx260 with the proprietary nvidia driver.

Specs:
Kubuntu 11.04 Natty
AMD Athlon64 X2 4800 2.4 ghz
2GB RAM
Shitty ASUS mobo

---

### Post by bailout on 2011-05-04
I have similar problems but only when resizing terminals, either konsole or xfce terminal but not xterm. There are a couple of threads on kubuntu forums with similar problems and links to bug reports.

[http://kubuntuforums.net/forums/index.php?topic=3116570.0](http://kubuntuforums.net/forums/index.php?topic=3116570.0)

[http://kubuntuforums.net/forums/index.php?topic=3116564.0](http://kubuntuforums.net/forums/index.php?topic=3116564.0)

---

### Post by BigErn on 2011-05-04
Looks like an Nvidia driver bug.  Thanks for the help!

:popcorn:

---

