---
title: "par2 limited to current directory - alternatives? (forward error correction)"
date: 2009-03-22
forum: General Help
---

### Post by kung fu buntu on 2009-03-22
When I used windows (a long time ago) I remember using quickpar, a par2 application, to create forward error correction archives, before burning important files to cd/dvd.

Now I would like to do the same thing in Linux. But to my dismay, par2cmdline (the par2 package) doesn't support recursion, that means you're stuck to the current directory.
The manual meantions that:
> This  version  of  par2  does not support recording path information for files. Whilst you can create recovery files for files from multiple locations, it will expect all files to be in the current directory when verifying and repairing. This limitation will be corrected in an update.
Unfortunately this was never fixed :(

Is there any branch of this code that I'm not aware off?
Is there a better alternative to par2?

Thanks!

---

### Post by kung fu buntu on 2009-09-20
The following fork of par2commandline fixes this problem:
[http://www.chuchusoft.com/par2_tbb/](http://www.chuchusoft.com/par2_tbb/)

It supports:
- concurrent processing
- Unicode
- hierarchial directory
It also allows for finding additional (aka renamed files or directories).

I've played with it and it worked perfectly.
Amazing piece of software! :D

Thread is fixed :D

/now off to find a decent incremental backup system to DVD (where rdiff fails and dar becomes kind of useless due to its container approach :p)
dkopp seems to do the trick... still have to test it

---

