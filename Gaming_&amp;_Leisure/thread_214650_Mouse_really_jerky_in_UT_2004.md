---
title: "Mouse really jerky in UT 2004"
date: 2006-07-12
forum: Gaming &amp; Leisure
---

### Post by BlueStreak on 2006-07-12
I just installed UT 2004 on my laptop.  I'm not expecting stunning game play here as I have no dedicated graphics card (just shared memory).  Otherwise it's a 1.86 Ghz mobile M proc. with 1 gig RAM.

Before Ubuntu I had XP pro and was able to play UT GOTY satisfactorily.  Had to keep the effects turned low but it ran pretty smooth and I was satisfied.  

Now that I have just Ubuntu (ext3) on this machine I tried ut 2004.  Installation seemed to go fine but when the game is running, even just going through the menus the mouse is EXTREMELY jerky.  I ran the game anyway and everything was fairly smooth, as good as can be expected on this machine except the mouse movements. It was intolerable

Just to be sure I tried a different mouse to no avail.  

That's the main problem.  2 other things.

1.  After installation I rebooted and suddenly sound no longer worked in the game but works elsewhere (XMMS etc.)

2.  This is a big WTF but my top and bottom task bars went from transparent to flourescent green!  Can't seem to get them back to transparent

Thanks!

--Update--Restarted X again and task bars went back to normal.  Disregard #2 :)

--Sorry, 'nother update-- Tried once more to run the game, same horrible mouse action and no sound.  Exited and task bars again turned hideous flourescent green.  They remain this way until x is restarted.

---

### Post by BlueStreak on 2006-07-13
When I installed this it was in the default C:/UT2004 directory.  Since this drive is exclusively linux (ext3) could that have something to do with it?  I would really appreciate some help

---

### Post by BlueStreak on 2006-07-13
Sorry about the bump but I have no idea how to resolve this.

Thanks!

---

### Post by seanj on 2008-01-13
I have this problem too, but no idea how to fix it. My graphics card is NVIDIA GeForce 8600 GT and CPU is AMD Athlon 64 3800+ 2.4 Ghz. So it's not just hardware issues. I think mouse control for UT2004 on GNU/Linux is just borked.

---

### Post by Cappy on 2008-01-13
I had this problem when I started using Ubuntu and it was all of the "CPU monitoring" applications I had running on the desktop.

Another thing is you will want to kill compiz-fusion before you launch ut2004.
```
metacity --replace
```
should do it.

---

### Post by seanj on 2009-09-16
Something I found that helped the mouse control in UT2004 was to uncheck both "reduce mouse lag" and "mouse smoothing" in the control settings.

---

