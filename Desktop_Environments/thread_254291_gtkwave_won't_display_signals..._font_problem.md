---
title: "gtkwave won't display signals... font problem?"
date: 2006-09-09
forum: Desktop Environments
---

### Post by theosib on 2006-09-09
I've been using gtkwave for a long time.  I just switched it Kubuntu, and I want to continue using it, but the one available from ubuntu seems to be broken.  I have a perfectly valid wave dump file, but I can't get gtkwave to show me any signals, and I think it might have something to do with these errors it keeps spitting out:

(gtkwave:6101): Gdk-CRITICAL **: gdk_text_width: assertion `font != NULL' failed

(gtkwave:6101): Gdk-CRITICAL **: gdk_text_width: assertion `font != NULL' failed

(gtkwave:6101): Gdk-CRITICAL **: gdk_text_width: assertion `font != NULL' failed

Is KDE exporting a font to this GTK application that it can't deal with?  How can I diagnose and fix such a problem?

---

### Post by GoJian on 2006-09-18
Actually you have to go to "Search" on the menu and do a "Signal Search Tree" and have your signal displayed.

I was thinking it was some font problem, too...  Why doesn't gtkwave just have all the signals displayed at startup?  Wasted me a whole afternoon debugging my verilog files...

---

