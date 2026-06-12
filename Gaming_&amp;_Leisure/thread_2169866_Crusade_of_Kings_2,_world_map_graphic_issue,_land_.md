---
title: "Crusade of Kings 2, world map graphic issue, land masses render black"
date: 2013-08-23
forum: Gaming &amp; Leisure
---

### Post by Karasawa7 on 2013-08-23
What I'm running:
Ubuntu 12.04.
Dell Inspirion 1750 laptop, Intel(R) Core(TM)2 Duo CPU, VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07).

The game is Crusade of Kings 2, a massive and super indepth conquering game that's awesome. I just bought it because I love the other games in the series. The game boots up just fine, the sound plays just fine, everything works the way it should....but...


This is what I *Should* be seeing.
[ATTACH=CONFIG]245646[/ATTACH]
This is what I see. Note the black, there should be country borders and stuff all over the map. But it's black (minus the overlay objects)
[ATTACH=CONFIG]245645[/ATTACH]

This was downloaded via steam, I paid $40 for it, and it's supported for linux. I want to blame my graphics card, or lack of, but I'm pretty sure this can be fixed....

Any ideas?

---

### Post by oldrocker99 on 2013-08-23
Try this:

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
[enter your password, and hit RETURN when asked)

sudo apt-get update && sudo apt-get upgrade

This **may** upgrade the Intel video drivers; I first heard about this PPA from Steam itself. Bear in mind that Linux Intel graphics drivers are all open source, with code and data supplied to Linux devs by Intel itself.

---

### Post by Karasawa7 on 2013-08-23
Did the code, it downloaded a bunch of stuff, then the Ubuntu automatic update manager popped up with stuff. 40mb. Let me download, restart, and get back to you.

---

### Post by Karasawa7 on 2013-08-23
Unfortunately, the land masses still render black. 
I thank you, however, for your help!

I do appreciate it. It's probably my system. I don't like integrated graphics.

---

