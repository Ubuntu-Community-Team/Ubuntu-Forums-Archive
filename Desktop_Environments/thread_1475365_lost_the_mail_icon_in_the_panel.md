---
title: "lost the mail icon in the panel"
date: 2010-05-06
forum: Desktop Environments
---

### Post by DomesDKG on 2010-05-06
I accidentally removed the little mail logo that monitors Empathy and Evolution from the Panel, how do I put it back?

---

### Post by finlost on 2010-05-06
I did the same.  I reset the panel to default.

> **jamieleshaw said:**
> Don't know if this is helpful but I will put it in anyway.
To Reset Panels type
rm -f ~/.gconf/apps/panel
then type
sudo /etc/init.d/gdm restart
;)

---

