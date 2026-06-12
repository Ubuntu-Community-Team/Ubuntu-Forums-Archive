---
title: "Strange problem with Mathematica"
date: 2006-10-05
forum: Education &amp; Science
---

### Post by kd5ezk on 2006-10-05
I have a really strange problem with Mathematica notebooks on Ubuntu.  If I scroll the notebook window back up, everything in the notebook display window suddenly "scrambles" (no problem scrolling down).  I can correct it by simply re-sizing the window, but it's very annoying.  Does anyone have an idea on how to fix this? (see attached images for examples)

---

### Post by jpkotta on 2006-10-05
I have the same problem on my desktop.  The problem there is the Composite extension to X.org.  It's not a problem with just Mathematica.  Any Motif (or Lesstif maybe?) program has the same problem with Composite (Nedit in my case).  All I can recommend is turning Composite off, or just being careful with using the scrollbar.  The problem only happens to me when I drag the scrollbar, but not when I click in the scrollbar or the scrollbuttons (and when Mathematica resizes/repositions things sometimes).

---

### Post by jpkotta on 2006-10-07
Found a fix and added it to the wiki: [https://help.ubuntu.com/community/Mathematica#head-f257f6630497b04601075cc9a92b88a26e60e21b](https://help.ubuntu.com/community/Mathematica#head-f257f6630497b04601075cc9a92b88a26e60e21b)

---

