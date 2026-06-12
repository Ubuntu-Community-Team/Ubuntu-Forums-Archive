---
title: "Odd shutdown/restart issue"
date: 2009-01-25
forum: General Help
---

### Post by Procuro on 2009-01-25
Hi all,

So when I shutdown ubuntu, everything is fine until the computer restarts and it hangs at the bios and freezes the desktop everytime. When I shutdown and restart in windows, everything is oddly enough ok and it restarts just fine. Is there anything I can do about it? Powering off the machine completely and restarting it fixes the problem so its really more of an annoyance if anything. Thanks!

---

### Post by mb_webguy on 2009-01-25
If it freezes during POST (i.e. while the BIOS is booting up), then it's not (directly) a problem with Ubuntu.  Are you sure it's not stalling at or after the GRUB menu?

I have had a vaguely similar problem when booting into Ubuntu after Windows failed to shutdown properly (caused by an issue with the NTFS filesystem), but in that instance the computer still made it through POST...

---

### Post by Procuro on 2009-01-25
It is for sure stalling before I even see the grub menu, it freezes right when the display pops up and says "hit F2 to enter setup" or something close to that.

I actually just discovered there are about 3 newer bios updates then the one currently on my machine. I'm gonna update it right now and see if that solves it. Thanks for the reply!

---

### Post by Procuro on 2009-01-25
Woot, updating the bios fixed it! I have an intel dg31pr and it fixed that issue along with my tv tuner hanging and a bunch of other stuff. I'm glad it was as easy as that :)

---

