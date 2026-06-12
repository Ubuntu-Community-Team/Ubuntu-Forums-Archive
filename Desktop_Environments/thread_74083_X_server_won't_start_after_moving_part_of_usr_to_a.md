---
title: "X server won't start after moving part of /usr to a new partition"
date: 2005-10-10
forum: Desktop Environments
---

### Post by Kensey on 2005-10-10
In an effort to get some usable free disk space, I carved a slice off my Windows partition, formatted it as ext3, and moved a couple chunks of /usr onto it like so:

/usr# find lib -depth -print | cpio -pmdV /opt/usr/lib
/usr# find share -depth -print | cpio -pmdV /opt/usr/share
/usr# ln -s /usr/lib /opt/usr/lib
/usr# ln -s /usr/share /opt/usr/share

This created /opt/usr/share and then put a share directory in it (same thing for lib) -- not what what I wanted, and broke a bunch of stuff.  So I did this:

/opt/usr# mv lib lib.skel
/opt/usr# cd lib.skel
/opt/usr# mv lib ..
/opt/usr# cd ..
/opt/usr# rmdir lib.skel

and likewise for /opt/usr/share.  After that /usr/lib and /usr/share symlinked to /opt/usr/lib and /opt/usr/share in the correct manner.

Now it *looks* like almost everything starts fine (for example ALSA was broken before, but now starts without error), but the system still complains about not being able to set some locale-related stuff, and the X server won't start (it tries what looks like 3 times, then pops up an ncurses dialog that says "do you want to see the X server output?" and locks up -- I have to Alt-Sysrq-B to restart).  I see from some other posts in other fora that some of the shared-memory mumbo-jumbo takes place under /usr -- have I hosed that by moving /usr/lib and /usr/share and symlinking them?  Has cpio messed up the copy somehow?

---

