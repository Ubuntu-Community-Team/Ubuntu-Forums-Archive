---
title: "WoW using DirectX"
date: 2007-08-23
forum: Gaming &amp; Leisure
---

### Post by MemoryDump on 2007-08-23
Today I decided to try running WoW without the OpenGL variable in the Config.wtf file (do to that DISCONNECT issue earlier today) and guess what? It actually appears to run smoother on my system!! :D

The ONLY issue I've discovered is that when the game is loaded I get both the WoW ICON (a hand/glove) and my mouse cursor/pointer showing at the same time. Has anybody experienced this? Any way to fix it?

thanks
-MD

---

### Post by cogadh on 2007-08-24
I've had it happen when running Advent Rising through Wine but I still haven't found a way to fix it (yet).

---

### Post by hikaricore on 2007-08-24
If I'm not mistaken the two cursor bug in WoW was fixed a long time ago, which version of WINE are you using?

I specifically remember someone on the WINE dev team saying on these forums that it was resolved.

---

### Post by Nkari on 2007-08-24
Well in D3D, (The mode I get slightly further in), I find that I only have the gauntlet pointer, and not the double pointer.

However The pointer does look a little strange, sort of patchy and partially transparent looking, quite hard to describe really.

This is with a reasonably  up to date version of wine (whatever the current version was last weekend)

---

### Post by MemoryDump on 2007-08-24
> **hikaricore said:**
> If I'm not mistaken the two cursor bug in WoW was fixed a long time ago, which version of WINE are you using?

I specifically remember someone on the WINE dev team saying on these forums that it was resolved.
I'm using wine-0.9.43

when I change the config in WoW back to use openGL the double-pointer goes away :confused:
could it be a setting in winecfg somewhere?

---

### Post by hikaricore on 2007-08-24
> **MemoryDump said:**
> I'm using wine-0.9.43

when I change the config in WoW back to use openGL the double-pointer goes away :confused:
could it be a setting in winecfg somewhere?

Perhaps the bugfix I'm speaking of wasn't accepted into the WINE code.

That's about all I can think of.

---

### Post by MemoryDump on 2007-08-24
> **hikaricore said:**
> Perhaps the bugfix I'm speaking of wasn't accepted into the WINE code.

That's about all I can think of.
do you recall if this BUG was specific to WoW? I'd like to further investigate this issue :)

---

### Post by hikaricore on 2007-08-24
> **MemoryDump said:**
> do you recall if this BUG was specific to WoW? I'd like to further investigate this issue :)

Check through the posts of AndrewRiedi here: [http://ubuntuforums.org/member.php?u=270295](http://ubuntuforums.org/member.php?u=270295)

Here's a semi-recent one where he mentions his cursor patch getting accepted by the WINE devs.  I assumed at the time this resolved the issue.

[http://ubuntuforums.org/showthread.php?p=2941425](http://ubuntuforums.org/showthread.php?p=2941425)

---

