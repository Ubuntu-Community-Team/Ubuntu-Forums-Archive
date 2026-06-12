---
title: "Problem with Workspace Switcher - GNome on Ubuntu 7.10 Desktop 64Bit"
date: 2007-11-26
forum: Desktop Environments
---

### Post by lce on 2007-11-26
I set my Workspace Switcher app to 4 workspaces with the arrangement of row=2 column=2. After a restart my Switcher defaulted back to 2 workspaces but the bottom right quick switch icon showing => 2 rows with the top row showing the two workspaces and the bottom row is a blank box. I changed the number of workspaces again to 4 workspaces with the arrangement of row=2 column=2. (I change the config by right clicking on the switcher in the bottom right and selecting prefs). After a restart all 4 workspaces are there but the quick switch icon show 2 rows - The bottom half is the blank area - The top half, inside this area is the icon that should normally be displayed showing 2 rows by 2 columns but now those workspace blocks are very very small since they are half the size.

How do I get the bottom blank area gone. Playing with the switcher config prefs doesn't fix the problem.

Any ideas?

---

### Post by lce on 2007-11-27
Is there a config file that I can manually edit?

---

### Post by yngveman on 2007-12-04
Just turn off compiz "metacity --replace" and then right click in the bottom right corner on the workspace switcher. Make sure you set it to 1 workspace displayed in 1 row. Then start compiz "compiz --replace". That should fix it.

---

### Post by shafin on 2007-12-07
> **yngveman said:**
> Just turn off compiz "metacity --replace" and then right click in the bottom right corner on the workspace switcher. Make sure you set it to 1 workspace displayed in 1 row. Then start compiz "compiz --replace". That should fix it.
Also change the number of workspaces from compiz-config-settings-manager, from general options,and desktops,change the number of workspaces.
You can get compiz-config-setings-manager on synaptic

---

