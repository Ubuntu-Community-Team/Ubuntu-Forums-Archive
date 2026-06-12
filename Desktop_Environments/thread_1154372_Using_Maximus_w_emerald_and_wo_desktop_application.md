---
title: "Using Maximus w/ emerald and w/o desktop application launcher"
date: 2009-05-09
forum: Desktop Environments
---

### Post by AlejandroDelLoco on 2009-05-09
How do I keep Maxiumus working (i.e. hiding the titlebar so window-picker-applet can handle it a la the default in Ubuntu NBR) when I am using Compiz and Emerald and not using the somewhat clunky desktop app picker interface? I used the desktop switcher and it disabled the app picker (I'm using the menu instead) but I really want maximus to keep its functionality.

**[COLOR="Red"]UPDATE - FIXED[/COLOR]**
I was fooling around with gconf-editor and found the solution. I just needed to toggle the following schema:
apps > maximus > undecorate

---

