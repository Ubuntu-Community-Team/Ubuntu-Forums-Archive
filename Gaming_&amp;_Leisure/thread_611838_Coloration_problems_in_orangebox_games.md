---
title: "Coloration problems in orangebox games"
date: 2007-11-07
forum: Gaming &amp; Leisure
---

### Post by Dapman01 on 2007-11-07
I am having problems with Half Life 2 Episode 2 having bad coloring.  Rocks appear bright green, and there are just coloring glitches everyware.  My GPU is not overheating and Half Life 2 works fine. 
Can anyone help

---

### Post by mbradlcu on 2007-11-12
humm,, I'm not having the issue, could you tell me what vid card you're using, I have an nvidia card running100.14.19

---

### Post by aoanla on 2007-11-13
This sounds like a known problem with Half life 2 Episode 2 (and Portal and other games using that iteration of the Source engine).

The bug is here:
[http://bugs.winehq.org/show_bug.cgi?id=10033](http://bugs.winehq.org/show_bug.cgi?id=10033)

and the Half-life 2 Episode 2 page on AppDB is here:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9421](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9421)

As you can see, you need to disable GLSL and possibly set the copy of hl2.exe in the Episode 2 folder to "Windows98" mode with winecfg.
(Please read the AppDB page for more details.)

---

### Post by Dapman01 on 2007-11-13
Half life 2 works fine, Episode 1 works fine. But any of the orange box games when I play the color are all wrong.  In eppy 2 the rocks are green and the other colors are messed up too
In portal Everything has messed up colors
can anyone help

---

### Post by Mblackwell on 2007-11-13
Disable HDR.

---

### Post by Dapman01 on 2007-11-13
> **Mblackwell said:**
> Disable HDR.

Thanks for the reply, but that didn't work

---

### Post by aoanla on 2007-11-13
There are a few other threads here talking about this, as it happens.

Your problem is an example, probably, of this bug:
[http://bugs.winehq.org/show_bug.cgi?id=10033](http://bugs.winehq.org/show_bug.cgi?id=10033)

The solution appears to be to disable GLSL by the method given on the bug page, and then to run the games in Windows98 mode (set hl2.exe to Windows98 mode *not* Steam - Steam will refuse to run in this mode!) with -dxlevel 80

Remember, if you find a wine issue, it is usually helpful to look at the AppDB entry for the game or games in question:

eg, for Portal, 
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9432](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9432)

---

