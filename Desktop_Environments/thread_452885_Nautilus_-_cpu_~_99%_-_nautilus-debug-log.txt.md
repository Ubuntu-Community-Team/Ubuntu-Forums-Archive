---
title: "Nautilus - cpu ~ 99% - nautilus-debug-log.txt"
date: 2007-05-23
forum: Desktop Environments
---

### Post by bluecherry on 2007-05-23
Hi,

I'm not sure whether this is a bug or not, so I'm posting here first to see what you guys make of it.

My Hardware:
Mem: 757.3MB
CPU: Athlon 64 3200+

Ubuntu Feisty - Latest updates as of May 24th, 2007

**Nautilus is consuming between 65 and 99% of my CPU when displaying nothing but the desktop.**
It show icons but it doesn't show previews (just the replacement icon as if it was creating the preview).

When I started to look around I found a file "*nautilus-debug-log.txt*" which was continuously growing in size as long as nautilus was running.

*Extract from nautilus-debug-log.txt:*
```
0x888d438 2007/05/24 01:18:57.3609 (USER): debug log dumped due to signal 8
0x888d438 2007/05/24 01:18:57.3639 (USER): debug log dumped due to signal 8
0x888d438 2007/05/24 01:18:57.3667 (USER): debug log dumped due to signal 8
```

I found that in 1 second nautilus adds the same line_ up to 371 times_ (only timestamp is different)

01:18:56 - 294x
:55 - 336x
:54 - 371x
:53 - 261x
:52 - 270x
:51 - 290x
etc....


I then proceeded to run an strace and backtrace but I didn't get any wiser as to what the reason for this behavior might be.

*Extract from strace*
```
[pid 14557] 00:58:20.697112 <... gettimeofday resumed> {1179961100, 696982}, NULL) = 0
[pid 14567] 00:58:20.697178 <... write resumed> ) = 4096
[pid 14557] 00:58:20.697252 gettimeofday( <unfinished ...>
[pid 14567] 00:58:20.697325 write(23, "208 2007/05/24 00:58:16.0393 (US"..., 4096 <unfinished ...>
```

In the 15 seconds i straced nautilus (launched by strace, so this includes startup and showing desktop/home folder) nautilus...
* called the _gettimeofday_ function _ 30194 times_
* wrote the message "(USER): debug log dumped due to signal 8" _25182 times_ to nautilus-debug-log.txt

I've also got a backtrace but I don't understand what it is trying to tell me :D.

**Is there anybody out there that knows what is wrong and what i can do  to fix it?**
Maybe it's a bug, but I find it strange that I can't find a thing about it anywhere on the net.
... or maybe I'm not looking hard enough?

---

### Post by bluecherry on 2007-05-23
Ok, I am soooo sorry.

I **did **notive the bug "Nautilus + SVG files = crash"  at [http://bugzilla.gnome.org/show_bug.cgi?id=309575](http://bugzilla.gnome.org/show_bug.cgi?id=309575)

On my crowed desktop I** didn't **notice the svg I created yesterday until just now. And guess what, moving to a folder different from the desktop solves my issue :s.

Shame on me for opening this thread! :oops:

=REMOVE=

---

### Post by siman on 2008-01-28
> **bluecherry said:**
> 
Shame on me for opening this thread! :oops:



very nice of you, I had the same problem :-)

---

