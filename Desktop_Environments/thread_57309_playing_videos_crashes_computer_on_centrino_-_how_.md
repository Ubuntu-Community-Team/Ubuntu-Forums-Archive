---
title: "playing videos crashes computer on centrino - how to fix"
date: 2005-08-16
forum: Desktop Environments
---

### Post by jmcnaught on 2005-08-16
hi,

this is my first post here, so my apologies if this is in the wrong area.  i have two centrino laptops, and both of them were freezing whenever i played videos, especially if i switched to full screen.  this was happening under totem-xine, totem-gstreamer, xine, mplayer etc.

i figured it might be something to do with X Windows, and searched the ubuntu bugzilla.  sure enough, somebody else had this problem: [bug 11674](http://bugzilla.ubuntu.com/show_bug.cgi?id=11674).  apparently it's been fixed in xorg 6.8.2-34, but hoary only has 6.8.2-10.

instead of waiting for breezy (or fixed xorg packages for hoary?), one can fix this problem by changing the video sink.  goto the system menu, click preferences, then choose "multimedia system selector".  on the video tab, change the output to "SDL Simple DirectMedia Layer".  this has worked for me on totem-gstreamer and totem-xine (i didn't test the xine engine for very long)

cheers,

jeremy mcnaughton

---

