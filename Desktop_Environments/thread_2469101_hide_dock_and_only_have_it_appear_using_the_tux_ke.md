---
title: "hide dock and only have it appear using the tux key"
date: 2021-11-19
forum: Desktop Environments
---

### Post by bigrockcrasher on 2021-11-19
I guarantee this has been asked before but I could not find a matching thread. I am using Ubuntu 20.04. I have my desktop set up to hide the dock unless I have moved my mouse all the way to the left side which still is a bit annoying. Is there a way to hide the dock and have it only appear when I press the tux key. 

thank you

---

### Post by ActionParsnip on 2021-11-20
Which dock do you mean please?

---

### Post by bigrockcrasher on 2021-11-23
Oh sorry should have been specific. I am using Ubuntu 20.04.3 with GNOME 3.36.8. The dock I am referring to is I think also called a launcher. By default it's the bar that is on the left hand side of the desktop.  Thank you for responding

---

### Post by philhughes on 2021-11-24
I don't know of a way to really disable it, but in dconf, if you navigate to /org/gnome/shell/extensions/dash-to-dock/pressure-threshold and set it to the maximum value (1.79769e+308), that effectively disables it, for me at least.

---

