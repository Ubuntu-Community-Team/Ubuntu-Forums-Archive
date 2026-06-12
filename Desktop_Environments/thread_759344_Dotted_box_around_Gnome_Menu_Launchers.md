---
title: "Dotted box around Gnome Menu Launchers"
date: 2008-04-19
forum: Desktop Environments
---

### Post by BandD on 2008-04-19
First of all, this is a purely cosmetic annoyance.  But for an anal bugger like me, it gets to me at times ;)

This seems to have been an issue for a long time now.  I found this [bug report]("https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/18361") that details the exact issue I'm having.

My main question is how to implement a fix that was posted.  Here is the fix:

```
Just commented out:

-- button-widget.c --
401: || GTK_WIDGET_HAS_FOCUS (widget)
467-483: if (GTK_WIDGET_HAS_FOCUS (widget)) {...}

-- panel-menu-bar.c --
298: if (GTK_WIDGET_HAS_FOCUS (menubar)) ...

First removes the launcher's highlight when clicking on the menu-bar (still highlighted when pointing the mouse over the launcher).
Second removes the launcher's dotted focus border when clicking on the menu-bar (completely removes it - that's maybe not wanted).
Third removes the menu-bar's dotted focus border when clicking on the menu-bar (completely removes it - that's maybe not wanted).
```

The thing is, I don't know where these settings are stored to begin with.  So if someone can help he out that would be greatly appreciated!!!

---

