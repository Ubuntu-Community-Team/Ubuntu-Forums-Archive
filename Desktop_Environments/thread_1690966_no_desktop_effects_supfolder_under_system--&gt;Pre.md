---
title: "no desktop effects supfolder under system--&gt;Preferences"
date: 2011-02-19
forum: Desktop Environments
---

### Post by boywithsling on 2011-02-19
I am trying to get compiz to automatically run on startup, this guide:  , told me to go to system-->preferences-->desktop effects-->enable desktop effects, but the subcategory "desktop effects" does not appear under preferences, neither does session, which several ether threads referred to people[.]("https://help.ubuntu.com/community/CompositeManager/CompizFusion")
I am running Ubuntu 10.10, it was installed as netbook edition but I went to system-->preferences-->Login screen--> select-->Ubuntu desktop edition. To save time, I have attached a screen shot of my preferences menu.

---

### Post by Frogs Hair on 2011-02-19
Hi and Welcome

Go to System > Preferences > Appearance > Appearance Preferences > Visual Effects.

If a driver is required , System > Administration > Additional Drivers or Hardware Drivers and install the recommended driver .

---

### Post by boywithsling on 2011-02-19
Ok, now how do I make it run on startup? I am using the command: *compiz --replace* to get it to run on for every session.

---

### Post by boywithsling on 2011-02-21
This worked, go to: System-->Preferences-->Startup Applications-->Add, and entered: ***compiz --replace*** in the command field. Thanks for your help Frog Hair.

---

