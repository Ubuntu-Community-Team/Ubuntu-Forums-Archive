---
title: "How do I install new themes for Gnome?"
date: 2006-05-30
forum: Desktop Environments
---

### Post by Flaringo on 2006-05-30
Hello. 

How do I install new themes and stuff for Gnome?


Thanks in advance.

---

### Post by dimebar on 2006-05-30
download them from art.gnome.com (or wherever)

open the containing folder in nautilus (places -> flaringo's home)

open the theme manager (system -> preferences -> theme)

click the theme details tab in the theme manager

if the theme is a set of controls, drag it into the list of controls (under the controls tab), same goes for window borders and icons (with their lists respectively)

---

### Post by ComplexNumber on 2006-05-30
[quote=dimebar]download them from art.gnome.com (or wherever)

open the containing folder in nautilus (places -> flaringo's home)

open the theme manager (system -> preferences -> theme)

click the theme details tab in the theme manager

if the theme is a set of controls, drag it into the list of controls (under the controls tab), same goes for window borders and icons (with their lists respectively)[/quote] for the most reliable results, i don't think thats the best idea in all cases. i recommend that he manually extracts them into any temporary folder, then places them in his /home/<username>/.themes folder. the reason why is that the install the them via the theme manager doesn't work in all cases. and the reason why iot doesn't work is that some themes contain more than one theme. for example, there's a theme called 'ish' that conatain ish, ish-blue, ish-red, etc. the theme manager can only deal with a tarball that has 1 and only 1 theme in it.
if he wants to install them so that all users have access to the theme, then he should install them in /usr/share/theme instead of /home/<username>/.themes. he will need to use 'gksudo nautilus'(DO NOT use sudo naultilus) to move them to that location.

---

### Post by astoltz on 2006-05-30
Try this trick...  Open the themes preferences.  Then browse around at gnome-look.org (or art.gnome.org) 'till you find a theme you like.  Drag the theme's download link from firefox to the theme window.  All done.

All the warnings that ComplexNumber points out still apply, but it'll work most of the time.

---

