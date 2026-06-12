---
title: "Simulating faster system time in terminal execution."
date: 2012-11-02
forum: Education &amp; Science
---

### Post by RobinBGH on 2012-11-02
Hello,

here's an odd question:

Is there a way to simulate a faster system clock when executing programmes from a terminal emulator such as bash/tcshell/etc?

Suppose you have written a programme ages ago and in order to ensure that buffers clear in time and there are no thread termination problems, you have included system clock-based waiting times at certain parts of the programme.

Years later you would like to re-run some experiments but reckon your computer today could do the whole thing much, much faster. Only you have specified these times in ms. So you need a way to make the programmes "believe" in a faster-than-real clock time.

Sadly, I was not very convinced of the necessity of good programming style back then. So I am sitting in front of folders and folders of different versions of the final compiled code. And I am not at all sure how it all fits together, and which versions of certain sub-functions I have actually used in the final programme. So re-compiling would take some serious retro-engineering...

Any ideas?

Cheers,
Robin

---

