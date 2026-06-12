---
title: "Quake2 segmentation fault when loading Outer Courts"
date: 2007-05-13
forum: Gaming &amp; Leisure
---

### Post by DrSnuggles on 2007-05-13
I've installed Quake 2 on my Feisty-setup. It works great (sort of, except some strange lighteffects because of the ati-drivers) but now I have a big problem!

I've played about 90% of the game, but when I finish the map which is second to last (strike - Outlands) the game quits. 
```
Outer Courts
Refusing to download a path with ..
Refusing to download a path with ..
Segmenteringsfel (core dumped)

```
This is REALLY annoying since I wanted to finish the game. Any suggestions?

---

### Post by mbradlcu on 2007-05-18
yea that would chap me too,, serious sam1 was like that,, anyway, if could tell me how to load that map I could see if it's happening to me,, if it doesn't then maybe we can compare configs to hopefully find out why.
thanks
Matt

---

### Post by DrSnuggles on 2007-05-18
Well... If I load the map manually it works, but then I can't continue to the next map because of "unfinished objectives" at the last one...

---

### Post by Andrew_P on 2011-02-03
I'm seeing the same problem in Windows 98SE, with Quake II patched to version 3.20.  I wrote a script to load each map in sequence and execute the "viewpos" console command while logging the console results to qconsole.cfg.  Sometimes it gets through all 39 levels without a problem; at other times it fails at some random level with the "Refusing to download a path with .." message.  Sometimes Quake II hangs when it issues the message, and at other times it continues the script to the next command.  The only thing I found that guarantees that it can execute the script to the end when this occurs is to restart Windows.  I think it's a problem in the Quake engine, probably a memory leak or difficulty allocating memory when the system has been up and running for a while.  The same may hold true for Linux.

---

