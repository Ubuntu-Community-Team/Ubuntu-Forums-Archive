---
title: "Hicolor/Truecolor error in Wine"
date: 2007-04-07
forum: Gaming &amp; Leisure
---

### Post by joaostoltz on 2007-04-07
Hi,
I am trying to use Flashback (yeah I know, old game but still cool) with wine.
I have Ubuntu 6.10 Edgy, and i have loaded Wine into it.

When I try to run Flashback (old DOS application, ran under Windows 95 also if I remember right) I get the following screen:

[ATTACH]29160[/ATTACH]

There is nowhere to change the color setting, only resolution. What should i do?

---

### Post by SishGupta on 2007-04-07
try either

start winecfg and on the applications tab try a different version of windows

or use dosbox

sudo apt-get install dosbox

---

### Post by joaostoltz on 2007-04-07
Got it fixed by changing xorg.conf file, there is line for it. :)

---

