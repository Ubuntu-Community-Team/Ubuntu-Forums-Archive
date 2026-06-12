---
title: "8-bit characters not visible under CTWM"
date: 2009-06-21
forum: Desktop Environments
---

### Post by wacky_keyboards on 2009-06-21
Hello,

I am running a 64-bit Ubuntu installation (Jaunty Jackalope) with GDM disabled so that I can use CTWM (my favorite window manager from the 90s) instead of Gnome.  (I downloaded CTWM using aptitude.)  For more details, see

[http://ubuntuforums.org/showthread.php?t=1190316](http://ubuntuforums.org/showthread.php?t=1190316)

I have a directory containing files with 8-bit characters, and I noticed that when I list them using "ls" under an xterm, only spaces are printed.  However, when I restarted GDM and logged back in under the usual (Gnome-based) method and listed the directory under an xterm, the 8-bit characters are printed as expected.

A Google search turned up this note from 2004 about 8-bit characters not appearing in strings displayed by CTWM's icon manager (although there is no mention of 64-bit OSes):

[http://tigerdyr.wheel.dk/ctwm-archive/0624.html](http://tigerdyr.wheel.dk/ctwm-archive/0624.html)

Is it possible that this issue is still affecting CTWM, possibly only for 64-bit builds?  Should I try to download the source and build it myself?  (I guess I would also need to test whether my installation of m4 is 8-bit clean.  Is there a good test for this?)

Thanks!

---

