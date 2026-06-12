---
title: "Broke Compiz, not sure how to fix/reinstall"
date: 2012-10-03
forum: Desktop Environments
---

### Post by jasonjob on 2012-10-03
I've managed to break Compiz.

Yesterday I got a system message saying that my / partition was nearly full.  While trying to to find out what had taken all my drive space (I use an 8 Gb partition for everything but /home), I ran across recommendations to use Ubuntu Tweak to clean up un-needed files.

As I already had it installed I figured I would use it.  And it worked; I cleaned out Firefoxes cache (800+ Mb, and I've since greatly limited the cache), and a bunch of old kernels (another 500 Mb or so).  I've now got well over 2Gb free again.

But it also purged allegedly un-needed packages.  After my next boot, Compiz just did not work.  Trying to start it with compiz --replace just gets a a lot of errors (couldn't load plugin libraries, no such file or directory, and apparently there are already handlers registered for most of what Compiz is trying to do) and no window manager.

So, I tried re-installing compiz's various packages, but it didn't work.  This morning I've gone through dpgk.log and re-installed the packages removed yesterday, but that didn't work either.

The only two options I can think of are a complete purge and re-install of Compiz (and Emerald, I suppose), or a clean install of Ubuntu.  I would rather not do the latter, but the former apparently involves uninstalling the ubuntu-desktop, so I'm a little apprehensive...

Thoughts?

---

### Post by jasonjob on 2012-10-03
Well dang, I fixed it.

Tried to run Catalyst Control Centre for my AMD card just to confirm that 3d graphics were working (I thought maybe I had a driver problem of some sort), and it couldn't start.

So I re-installed fglrx and the AMD stuff, and lo and behold Compiz is back.

Don't know what went wrong, and maybe it wasn't the janitor after all (but the timing suggests it was).

Ah well, it works again :)

---

