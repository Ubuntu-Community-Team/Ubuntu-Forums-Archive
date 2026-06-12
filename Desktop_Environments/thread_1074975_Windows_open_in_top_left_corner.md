---
title: "Windows open in top left corner"
date: 2009-02-19
forum: Desktop Environments
---

### Post by tad1073 on 2009-02-19
How do I get my application windows to open in the middle of my screen?

Or at least the first window.

Or how do I get conky to be always on top?

---

### Post by cph05a on 2009-02-19
I'm not sure that there is a setting for controlling where all your applications open. When you're writing an application using GTK+, you can specify where you want the window to open. The default location is the top left corner. 

If you're interested, here's how you can tell your own GTK app to open in the center:
```
gtk_window_set_position(GTK_WINDOW(window), GTK_WIN_POS_CENTER);
```

---

### Post by jeffjohnson on 2009-03-05
Did you ever get this fixed.  I am having the same problem.  It happened after I did a system Restore.

---

