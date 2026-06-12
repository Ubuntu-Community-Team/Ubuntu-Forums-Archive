---
title: "minor issue on gutsy: greyed out title"
date: 2007-10-15
forum: Desktop Effects &amp; Customization
---

### Post by icic on 2007-10-15
Hi there!


I have just installed Gutsy, and it's going great except for this minor annoyance when I enable "normal" visual effects.

The title bar of a maximized window occaisonally "greys out" (see screenshot)
[http://img463.imageshack.us/img463/7716/screenshotbe7.png](http://img463.imageshack.us/img463/7716/screenshotbe7.png)

This only happens when the window is maximized, and in any application (not just firefox)
It is only temporary and as soon as the window's title changes or i move the mouse over the title bar, it returns to its proper state.

I have an nvidia go 7200, and installed the nvidia driver through the restricted driver manager.



I had this problem when using compiz on feisty as well.

Thank you very much for your support!

Ian.

---

### Post by icic on 2007-10-18
anyone? cheers

---

### Post by icic on 2007-10-20
hi there

i managed to fix the problem

i downloaded and installed these packages:
libglitz-glx1 (0.5.6-1)
libglitz1 (0.5.6-1)
xserver-xgl (1:1.1.99.1~git20070727-0ubuntu3)

i have no clue how or why it works, but the problem seems to have gone away now.

---

### Post by 4KvRMU7Nnv on 2007-10-20
yes I confirm this works, however, this installs XGL as opposed to AIGLX which is inferior.

---

### Post by chriswyatt on 2007-10-20
I have the same problem as you, I think I'll just put up with it for now and hope the issue gets sorted out in a future update (fingers crossed), everything else seems to be running fine.  Noticed some major slowdown when playing Minesweeper fullscreen, with Compiz on.

BTW, I also have a GeForce Go 7200, and I have a Centrino Duo if that makes any difference at all.

---

### Post by pierceive on 2007-10-21
I have the same problem on my computer (using a PCIe GeForce 7900GS) as well as my wife's (onboard GeForce 6100). While the problem appears as soon as I turn on visual effects on my wife's computer, it only appears intermittently on mine.

---

### Post by BigSilly on 2007-10-22
I have this problem too. Has it been reported as a bug? I've never reported a bug before myself, but I guess it would be worth it. It's hard to pinpoint what triggers it though, since it seems to be fairly intermittent.

---

