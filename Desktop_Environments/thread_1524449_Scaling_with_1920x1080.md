---
title: "Scaling with 1920x1080"
date: 2010-07-05
forum: Desktop Environments
---

### Post by Oyb on 2010-07-05
Hi,

Was wondering if its possible to scale ubuntu theme/environment to suite 1920x1080. Im using my comp on a 42" plasma TV, and it gets kinda small with the default scale. 

Don't want to change to a lower res, simple because it's not as pretty and the toolbars are almost hidden.

---

### Post by jbo5112 on 2010-07-05
There should be a way to manually adjust the monitor size (or dpi/ppi).  If the computer thinks the screen is physically smaller, it will calculate it as having more pixels per inch and it should render a lot of things using more pixels (fonts, vector graphics).

I know this can be done in your xorg.conf file, but Ubuntu doesn't even use one unless you personally supply it.  I would hope KDE and Gnome supply something.

---

### Post by hictio on 2010-07-05
I'm not that expert when it comes to resolutions, video cards, etc. but, have you looked onto the dpi option on:

System > Preferences > Appearance > Fonts (tab) > Details

It is the first option on the new window that pops up.

---

