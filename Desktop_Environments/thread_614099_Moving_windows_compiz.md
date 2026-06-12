---
title: "Moving windows compiz"
date: 2007-11-15
forum: Desktop Environments
---

### Post by bwiklak on 2007-11-15
Hi,
When I want to move window, and I clink on title bar, window moves according to cursor but I need to click again to deactivate window wowing, I cant just drag windows. It`s very annoying. I use CompizFusion, in metacity everything is ok (after RightMouseButtonUp window stops moving).

How can I turn on "normal" window moving style?

---

### Post by jpietari on 2007-11-17
Do you have "compizconfig-settings-manager" installed?  I briefly looked at my configuration, but didn't see any option that you are describing.  I could've missed it though...

---

### Post by Forlong on 2007-11-17
Although I don't really understand the problem, try this [1]:

ccsm &#8594; Move Window &#8594; Actions

double-click **Initiate Window Move** and click on the brush (Reset To Defaults)


Hope it helps.


[SIZE="1"][1] in case you do not have ccsm installed:
```
sudo apt-get install compizconfig-settings-manager
```[/SIZE]

---

### Post by bwiklak on 2007-11-18
> **Forlong said:**
> 
ccsm &#8594; Move Window &#8594; Actions

double-click **Initiate Window Move** and click on the brush (Reset To Defaults)


Wow, that helped! Thanks a lot.

---

