---
title: "Run sutom sommand on resolution change?"
date: 2008-02-08
forum: Debian
---

### Post by pepsi_max2k on 2008-02-08
Hey all, does anyone know of a way I could run a custom command (eg. "xbv DIS_FFILT 1") when the X resolution changes?

I'm running Xebian 1.1.4 on an xbox, using ratpoison desktop and XFree86.

Bit of background - I'm using the xbox for a mythtv frontend, and because it's mainly for video watching on a CRT tv I want to disable the inbuilt flicker filter for video, but enable it when I'm back in the gui as it, well, flickers, in some cases a lot, without any filter.

I've not yet found any way to run custom commands when switching between video and mythui in myth, but I can have it change resolution between the two (which i actually need it to do due to a corruption bug when using my video's native resolution for the gui). Soo... I'm thinking monitor X for resolution change (at the very least i know it makes a record of this in /var/log/XFree86.0.log) and whenever it changes, run the appropriate command. And because it's a 64M ram xbox, anything that uses as little memory as possible is good :)

Thanks.

---

