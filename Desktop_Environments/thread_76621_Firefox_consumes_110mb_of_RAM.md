---
title: "Firefox consumes 110mb of RAM"
date: 2005-10-15
forum: Desktop Environments
---

### Post by fnando on 2005-10-15
I opened Firefox with 6 tabs and System Monitor shows 110mb of RAM consumption.
The same 6 tabs opened on WinXP show 24mb. No flash page opened. Just HTML.

Is that normal? I mean, is 5x more.

---

### Post by SilentCacophony on 2005-10-15
I can't compare it to XP, but in Ubuntu, here is what I get without Firefox open:

```
brian@ubuntu:~$ free
             total       used       free     shared    buffers     cached
Mem:        451852     398104      53748          0      66052     180352
-/+ buffers/cache:     151700     300152
Swap:      1020088          0    1020088
```

Here is what I get with Firefox open, with 6 tabs open from various parts of these forums.

```
brian@ubuntu:~$ free
             total       used       free     shared    buffers     cached
Mem:        451852     417612      34240          0      66148     181412
-/+ buffers/cache:     170052     281800
Swap:      1020088          0    1020088
```

user ram usage went from 151700 to 170052

---

### Post by GeneralZod on 2005-10-15
How long have you had it open for? Firefox leaks memory like a sieve, so this could be the cause.

---

### Post by fnando on 2005-10-15
[QUOTE=GeneralZod]How long have you had it open for? Firefox leaks memory like a sieve, so this could be the cause.[/QUOTE]

Firefox stays opened all the time! ;) I'm webdeveloper so is impossible not to do that!

Thunderbird is consuming lots of RAM too! 
136.2mb of RAM and 79% CPU. I just opened (less than 1 minute opened) :-(

---

### Post by VR6Pete on 2005-10-15
My firefox is using well over 100MB too. only browseing this site for a few minutes...

---

### Post by khc on 2005-10-15
Install the session saver extension, and restart firefox at the end of each day :-)
On a machine with 512MB of RAM, I usually don't notice a problem. Right now I have 12 tabs opened.
Also any resource meter may not be accurate, since you don't know how much is paged to disk.

---

### Post by joelito on 2005-10-15
[quote=khc]
Also any resource meter may not be accurate, since you don't know how much is paged to disk.
[/quote]

Actually, the graphs on the sistem monitor (in at least gnome) have diferent graphs for swap and for physical memory, idealy swap is not used unless necessary

---

### Post by fnando on 2005-10-15
[QUOTE=khc]Install the session saver extension, and restart firefox at the end of each day :-)[/QUOTE]

I've got that extension! Can't live without it! ;)

I always thought that Firefox memory consumption problem was only to flash pages (because of flash plugin)

---

### Post by fnando on 2005-10-15
I attached a System Monitor screenshot.

---

### Post by Brent Dax on 2005-10-15
[QUOTE=fnando]I opened Firefox with 6 tabs and System Monitor shows 110mb of RAM consumption.[/QUOTE]
Unless I'm mistaken, all browsers on all platforms leak memory (it has to do with mismatches between Javascript's garbage-collected model and most browsers' internal reference-counted models), and no program on any platform returns memory to the OS.  In other words, Firefox's memory consumption will slowly creep up and never fall.

In other other words, don't worry so much about it.  Any memory Firefox leaks will be swapped out and probably never used again.

---

