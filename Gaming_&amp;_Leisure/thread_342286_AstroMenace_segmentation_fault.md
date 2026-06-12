---
title: "AstroMenace segmentation fault"
date: 2007-01-19
forum: Gaming &amp; Leisure
---

### Post by jjf on 2007-01-19
I found a really cool space scroller, free for Linux (shareware Win version).  It runs for a couple minutes, then crashes to the desktop with a segmentation fault.  I ran strace on it.  Here are the last few lines of the file:

```
gettimeofday({1169180369, 719147}, NULL) = 0
gettimeofday({1169180369, 719263}, NULL) = 0
gettimeofday({1169180369, 719480}, NULL) = 0
gettimeofday({1169180369, 719558}, NULL) = 0
gettimeofday({1169180369, 719623}, NULL) = 0
gettimeofday({1169180369, 720401}, NULL) = 0
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
rt_sigaction(SIGSEGV, {SIG_DFL}, {0xb7f0b6c0, [], 0}, 8) = 0
rt_sigaction(SIGINT, {SIG_DFL}, {0xb7f127c0, [INT], SA_RESTART}, 8) = 0
rt_sigaction(SIGTERM, {SIG_DFL}, {0xb7f127c0, [TERM], SA_RESTART}, 8) = 0
write(12, "_\1\2\0\v\0\0\3+\0\1\0", 12) = 12
read(12, "\1\1\236\0\0\0\0\0\16\0\0\3\0\0\0\0\0\0\0\0\4\0\0\0\274"..., 32) = 32
write(12, "\33\1\2\0\0\0\0\0 \0\2\0\0\0\0\0+\0\1\0", 20) = 20
read(12, "\1\1\241\0\0\0\0\0\16\0\0\3\0\0\0\0\0\0\0\0\4\0\0\0\274"..., 32) = 32
write(12, "\210\2\2\0\0\0\0\0+\0\1\0", 12) = 12
read(12, "\1\1\243\0\0\0\0\0\16\0\0\3\0\0\0\0\0\0\0\0\4\0\0\0\274"..., 32) = 32
write(13, "+\23\1\0", 4)                = 4
read(13, "\1\1\36\0\0\0\0\0\16\0\0\3\1\0\0\0\0\0\0\0\4\0\0\0\274"..., 32) = 32
write(13, "\217\5\4\0\0\0\0\0\0\0\0\0\1\0\0\0", 16) = 16
read(13, "\1\0\37\0\0\0\0\0\1\0\0\0\0\0\0\0p\264D\10@\262D\10\200"..., 32) = 32
brk(0xb7e2000 <unfinished ...>

```

But I have no idea where to go from here.  Anything I could do to fix this?  Neverwinter Nights also experiences random crashes on me after 5-30 minutes of play.  Could they be related?

And what's with all the calls to gettimeofday()?  (There are [S]hundreds[/S] **tens of thousands** of them in the trace file.)

---

### Post by www.rzr.online.fr on 2008-06-02
I can help on this package I built at :
-- 
[http://rzr.online.fr/q/openal](http://rzr.online.fr/q/openal)

---

