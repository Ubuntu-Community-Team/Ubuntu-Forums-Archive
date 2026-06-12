---
title: "NVidia Artifacts:  New windows are often corruped for about a second"
date: 2008-12-05
forum: General Help
---

### Post by atorch on 2008-12-05
Hi,

Please see [http://www.nvnews.net/vbulletin/showthread.php?t=123009](http://www.nvnews.net/vbulletin/showthread.php?t=123009).

> For those who don't get this bug: on 177.80 with a compositing manager enabled, the content of newly created windows is sometimes replaced with corrupt graphical mess for a split second. It's not critical but it's annoying. Nvidia has acknowledged the existence of this bug in 177.80 beta release forum post and it's still not fixed.

I experience exactly what is described above, on both Gutsy and Intrepid.  I'm currently running compiz & version 177.80 of the nvidia driver.

Does anyone else suffer this bug?  I imagine it would be a problem for many people, since nvidia + compiz seems like a fairly common combination.

When will this be fixed?  As he says in the quote, it's not critical, but it is extremely annoying and it makes my Ubuntu ugly.  Big sad face.

---

### Post by atorch on 2008-12-06
Anyone?  I'll try to get an image, but it's difficult unless I can find a way to screen capture at a very high frame rate.  (Or get really lucky with a single screenshot.)

The "corrupt graphical mess" is usually recognizable:  parts of windows that are no longer open, for example.  When I open evolution, I might see pieces of a firefox window that was running earlier (but is now closed).

Edit:  hopefully the 180.11 driver will be in the Intrepid repos soon, see [http://ubuntuforums.org/showthread.php?t=1002500&highlight=180.11](http://ubuntuforums.org/showthread.php?t=1002500&highlight=180.11).

---

### Post by atorch on 2008-12-17
Fixed with 180.16 (beta) nvidia drivers, see [http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia+artifacts](http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia+artifacts).

---

