---
title: "Missing Panel"
date: 2009-01-04
forum: General Help
---

### Post by djangolucas on 2009-01-04
I installed the newest version of Ubuntu and after the installation I can no longer have the top panel with menu choices/applications. I have a desktop but not panel at the top or bottom of my screen. I've been looking online but I can't figure out what the problem is.....everything is fine in KDE but when I start a session in gnome I can't seem to find any way to get the panels on my desktop. Any one run into this with the new install or have any suggestions?

---

### Post by fooman on 2009-01-04
try pressing alt-f2 and see if a "run program" dialog box pops up.  if it does,  type the following into it and press "run":

```
gnome-panel &
```

hope that helps.

---

### Post by cariboo on 2009-01-04
Have you tried in a Applications-->Accessories-->Terminal:

```
gnome-panel
```

The reason for running it in a terminal is to see what error message you get if any.

Jim

---

