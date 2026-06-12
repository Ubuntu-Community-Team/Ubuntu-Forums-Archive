---
title: "Is it possible that some windows games run faster with wine than natively on XP?"
date: 2005-05-27
forum: Gaming &amp; Leisure
---

### Post by NoTiG on 2005-05-27
just curious if anyone has benchmarked and seen if a game is actually FASTER on linux than windows.

---

### Post by magomago on 2005-05-27
that can't be possible using the same machine.  Wine adds a layer of emulation,interpreation,bla bla bla.  What it is exactly, it is more overhead for the compuer to deal with so wile I can see a game running close to 100%, maybe 99%...I can't see it running FASTER with MORE overhead.

---

### Post by skirkpatrick on 2005-05-27
Wine doesn't run as an emulator.  What it provides is the Windows API and .dll's needed to run the software.  The code runs natively on your hardware.  Now that doesn't mean that the API calls and .dll's are as optimized as they can be under Windows (but it also means that they might be more optimized).

The only FPS that I've tried so far is Call of Duty.  I do get slightly higher and more consistent framerate under Cedega than I did in XP Pro.  I also don't get 5 minutes of Punkbuster lag when I first connect to a server like I do in XP.

---

### Post by NoTiG on 2005-05-28
[QUOTE=skirkpatrick]Wine doesn't run as an emulator.  What it provides is the Windows API and .dll's needed to run the software.  The code runs natively on your hardware.  Now that doesn't mean that the API calls and .dll's are as optimized as they can be under Windows (but it also means that they might be more optimized).

The only FPS that I've tried so far is Call of Duty.  I do get slightly higher and more consistent framerate under Cedega than I did in XP Pro.  I also don't get 5 minutes of Punkbuster lag when I first connect to a server like I do in XP.[/QUOTE]

Seeee. :P i find that very interesting. It would be cool to experiment with optimizations.. like the reiser filesystem.. or maybe using gcc 4.0 to compile the kernel or other things. It would be cool if other ppl posted their experiences :P

---

### Post by Moobert on 2005-05-28
people have run benchmarks on the wine dx9 patches:

[http://www.linux-gamers.net/modules/news/article.php?storyid=793](http://www.linux-gamers.net/modules/news/article.php?storyid=793)

the results give random results, you can probably put this down to parts of the wine API being better, others not so good... But wine is always beng updated, along with linux glx, so in a few years who knows.

Myself i found that ut2004 runs about 10 to 30% faster on linux than windows (thats native, not using cedega)... with one of the benchmarks i found about an 10fps increase using linux cedega... but then looking at hl2 i get a about a 50% decrease in fps using cedega (mind you hl2 coding is doggy at best :)

---

