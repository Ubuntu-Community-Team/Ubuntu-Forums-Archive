---
title: "Beryl is broken"
date: 2007-07-15
forum: Desktop Effects &amp; Customization
---

### Post by TonyMontana on 2007-07-15
Beryl had been working for me ever since I installed Fiesty with no issues whatsoever.  Suddenly it stopped working completely... 

Entering 'beryl-manager' from the command line results in the Beryl icon appearing on the Gnome panel, but there are no desktop effects.  I can, however, run this command as root and it seems to work.

Entering 'beryl --replace' starts beryl but removes all my window borders.

I did nothing at all in the way of modifying my X configuration, nor have I upgraded any system software.  I did recently install WinXP on a VMware partition, but that shouldn't affect anything, should it?

My hardware...
AMD Athlon64 X2 Dual Core Processor 5200+
nVidia GeForce 7900 GT

---

### Post by locke.dragon on 2007-07-15
the install of xp shouldn't have affected it.  but you may want to look into compiz fusion.  beryl is pretty much dead now and compiz fusion will blow you away when compared with beryl.

[http://ubuntuforums.org/showthread.php?p=2895086](http://ubuntuforums.org/showthread.php?p=2895086)

just follow the steps above and you'll have it running in no time.  :D  there have been reports of beryl not working that great with a fresh install of feisty, but at this point in the game, it'd just be best to install compiz fusion.  it's awesome anyways.  ;)

---

### Post by ThrobbingBrain66 on 2007-07-15
> **TonyMontana said:**
> Beryl had been working for me ever since I installed Fiesty with no issues whatsoever.  Suddenly it stopped working completely... 

Entering 'beryl-manager' from the command line results in the Beryl icon appearing on the Gnome panel, but there are no desktop effects.  I can, however, run this command as root and it seems to work.

Entering 'beryl --replace' starts beryl but removes all my window borders.

I did nothing at all in the way of modifying my X configuration, nor have I upgraded any system software.  I did recently install WinXP on a VMware partition, but that shouldn't affect anything, should it?

My hardware...
AMD Athlon64 X2 Dual Core Processor 5200+
nVidia GeForce 7900 GT

Along with beryl --replace, also run emerald --replace and you should have window borders

---

