---
title: "How do I restore the network applet in the panel?"
date: 2010-05-05
forum: Desktop Environments
---

### Post by BikeMike on 2010-05-05
I had too many issues with 10.04 so reinstalled 9.10 for now.

In the process of customizing the panel, I accidentally deleted the network and sound icons and there isn't any option I can find in the menu to restore it. How do I go about getting those back?

Many thanks from a Linux user that isn't very technical. :)

---

### Post by finlost on 2010-05-06
> **jamieleshaw said:**
> Don't know if this is helpful but I will put it in anyway.
To Reset Panels type
rm -f ~/.gconf/apps/panel
then type
sudo /etc/init.d/gdm restart
;).

---

### Post by kid1000002000 on 2010-05-09
is network manager running in the background, or is the entire app not working?  you could try restarting the entire app.

---

