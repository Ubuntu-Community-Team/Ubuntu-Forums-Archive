---
title: "How do I move the app controls (X-close, BOX-fullscreen, UNDERSCORE-minimize to right"
date: 2014-07-07
forum: Desktop Environments
---

### Post by RogerDavis on 2014-07-07
How do I move the app controls (X-close, BOX-fullscreen, UNDERSCORE-minimize to right side of the and app bar?

New install of Ubuntu 14.04

---

### Post by deadflowr on 2014-07-07
Is this flashback, still, or unity?

---

### Post by RogerDavis on 2014-07-07
Flashback.

This works for 14.04 too:
For Ubuntu 12.10, 13.04 and 13.10

    Press Alt-F2, then type dconf-editor into the box, and press Enter to run it. (See Note below)
    Browse to org > gnome > desktop > wm > preferences, look for "button_layout" on the right panel.
    Change the value in the "button_layout" from close,minimize,maximize: to :minimize,maximize,close and press the Enter key.

---

### Post by deadflowr on 2014-07-07
So, solved?

---

### Post by RogerDavis on 2014-07-07
Yes, works fine...

---

### Post by deadflowr on 2014-07-07
[How-to mark a thread as solved, if solved and why]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

