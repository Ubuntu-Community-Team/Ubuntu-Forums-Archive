---
title: "Audition Online in Wine/Cedega?"
date: 2007-03-29
forum: Gaming &amp; Leisure
---

### Post by Xelinis on 2007-03-29
Anyone know how to get Audition Online working?  I seems to install just fine but it won't start at all.

---

### Post by Xelinis on 2007-04-03
Erm, anyone?

---

### Post by hikaricore on 2007-04-03
I looked around for you last week but forgot to reply.  >.<

I couldn't find any information on the game, but I believe it uses advanced direct 3d based code which is not very well supported by wine, it may be possible in cedega but you'll probably need to ask them if it is.

Sorry it looks like you may need to dual boot for this title unless you find a solution that I don't know of.

Good luck,

--Aaron

---

### Post by Xelinis on 2007-04-12
xelinis@Obsidian:~$ cedega

(Point2Play_gui.py:2893): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09; 
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
wine: Unhandled exception, starting debugger...
xelinis@Obsidian:~$ 


Here's what happens when I try running it in Cedega 6.  Any ideas folks?

---

### Post by AndrewRiedi on 2007-04-12
> **hikaricore said:**
> I looked around for you last week but forgot to reply.  >.<

I couldn't find any information on the game, but I believe it uses advanced direct 3d based code which is not very well supported by wine, it may be possible in cedega but you'll probably need to ask them if it is.

Sorry it looks like you may need to dual boot for this title unless you find a solution that I don't know of.

Good luck,

--Aaron

Aaron, wine-0.9.34 has *more* advanced D3D support than cedega 6.0.  For instance, wine has support for PS 3.0, where cedega only has support for PS 2.0.  Please do not imply that cedega has more advanced d3d than wine, because it clearly does not.  It may, however, still run games that wine does not.  This is not because it is more advanced, but because AJ does not allow hacks in the wine codebase.  Sometimes these hacks are needed in the short term until a real solution is found, and in these cases crossover and cedega can end up being the better choice.

Also, wine's alsa/dsound code is not very great right now, but wine has a Google SoC project to help fix that, but that has no relation to D3D other than they are both a part of directx.  What is holding wine's gaming back is not D3D, but all the other little stuff that needs to work perfect.  Installs, easy to use interface, cursor problems, sound, lack of a DIB engine, not accepting hacks into the main codebase, etc.

PS: I am not mad at you or anything, I just don't like FUD being spread around like this, and it annoys me.

---

### Post by hikaricore on 2007-04-12
> **AndrewRiedi said:**
> Aaron, wine-0.9.34 has *more* advanced D3D support than cedega 6.0.  For instance, wine has support for PS 3.0, where cedega only has support for PS 2.0.  Please do not imply that cedega has more advanced d3d than wine, because it clearly does not.  It may, however, still run games that wine does not.  This is not because it is more advanced, but because AJ does not allow hacks in the wine codebase.  Sometimes these hacks are needed in the short term until a real solution is found, and in these cases crossover and cedega can end up being the better choice.

Also, wine's alsa/dsound code is not very great right now, but wine has a Google SoC project to help fix that, but that has no relation to D3D other than they are both a part of directx.  What is holding wine's gaming back is not D3D, but all the other little stuff that needs to work perfect.  Installs, easy to use interface, cursor problems, sound, lack of a DIB engine, not accepting hacks into the main codebase, etc.

PS: I am not mad at you or anything, I just don't like FUD being spread around like this, and it annoys me.

I wasn't actually saying that cedega had better d3d support.  I also wrote this before the release of cedega 6.  I was trying to offer the OP a simple response as to why the title did not run in wine.  This was mostly due to me not having time to try it out myself and give a better reason.  So my answer was mostly BS, but I do see where this could cause some confusion.  I'll try to avoid responses like this in the future.  :)

p.s. I didn't actually suggest they try cedega either, I just mentioned it might be worth looking into.

---

