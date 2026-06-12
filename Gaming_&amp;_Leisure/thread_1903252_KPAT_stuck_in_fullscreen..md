---
title: "KPAT stuck in fullscreen."
date: 2012-01-02
forum: Gaming &amp; Leisure
---

### Post by Adam_GUI on 2012-01-02
I'm not sure how I managed it. It's fullscreen with no window border.  Telling it to unmaximize does nothing.  I have to ALT+Tab to another window to see my menu bar or avant-window-navigator.  

Reloading the window manager does nothing to help the problem.
Purging and reinstalling kpat does nothing.

Is there a presence or screen setup file I can delete to get kpat back to default window size?

---

### Post by Adam_GUI on 2012-01-03
I've just reacheda surreal google-fu zen by finding my own problem on page 1 in search results.

"Oh, great!  Someone had the same issue!  Maybe there's a solution!"

Nope.  Weird, oddly funny, just odd.

---

### Post by Adam_GUI on 2012-01-09
Problem solved.  Found my solution here:
[http://ubuntuforums.org/showthread.php?t=1049107](http://ubuntuforums.org/showthread.php?t=1049107)

Had to open ccsm, go into utilities, and uncheck legacy fullscreen support.
Now kpat, konqueror, and other kde applications get their borders back.

---

