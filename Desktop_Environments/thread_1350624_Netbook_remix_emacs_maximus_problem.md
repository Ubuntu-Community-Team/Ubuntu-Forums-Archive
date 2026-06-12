---
title: "Netbook remix emacs maximus problem"
date: 2009-12-09
forum: Desktop Environments
---

### Post by izahn on 2009-12-09
I'm running UNR on my Asus 900. I love maximus, except that it does not respect the emacs notification bar. That is, emacs is maximized in such a way that the notification bar extends off the bottom of the screen. I don't want to disable maximus, because in general I love it. But I need my emacs status bar! Any thoughts? Can maximus be customized? Even if I could tell it to just ignore (i.e., do not maximize) emacs that would be better.

Thanks!
Ish

---

### Post by wmgoree on 2009-12-09
If you're comfortable using gconf, you can edit the key /apps/maximus/no_maximize (or something like that; that's from memory) to exclude the applications you don't want maximized.

---

### Post by izahn on 2009-12-09
That works. Thanks for the help!

---

### Post by jim.hansson on 2010-07-19
Ubuntu netbook remix 10.4 still seems to have this problem.

In gconf-editor under apps/maximus/exclude_class I added "Emacs" to the list. This means other windows are still maximized but not emacs.

if you check the no_mazimize checkbox instead no window will be maximized.

---

