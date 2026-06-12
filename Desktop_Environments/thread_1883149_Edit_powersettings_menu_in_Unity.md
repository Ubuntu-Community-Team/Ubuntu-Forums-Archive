---
title: "Edit power/settings menu in Unity"
date: 2011-11-18
forum: Desktop Environments
---

### Post by jose lourenco on 2011-11-18
Hey there,

Is there any way of manually editing the power/settings in Unity?
(Ubuntu 11.10, top right corner menu)

Here is my problem:

Hibernate does not work via this menu, but it does using "hibernate --force" on a shell. Ive been hibernating the machine using a keyboard shortcut and would like either to EDIT or REMOVE the hibernate/suspend option in the menu since both do not work.

Any ideas?
thanks

---

### Post by gordintoronto on 2011-11-18
In my experience, starting from Hibernate takes just as long as a cold boot, so there's no benefit to it. Suspend should work, if your swap file is larger than your RAM. 

Is this a laptop or desktop? On my laptop, I close the lid, it suspends, open it, it starts up in just a few seconds.

And yes, there is a way to edit the settings, but I don't think it changes what appears in the menu.

---

### Post by jose lourenco on 2011-11-18
hey there

its a netbook and suspend does not work, the ATI driver for Radeon HD is messed up, never got it to run in any distro i ever tried

i use hibernate-disk cause it takes about 10 seconds to startup, much faster than a normal boot... 

so the question is not how to make it work, hibernate-disk is fine with me, i was just wondering if i could change the option in the menu or the system default which seems to run hibernate-ram instead...

---

### Post by Frogs Hair on 2011-11-18
I think the package is indicator-power , but it looks like an all in one package and I don't know if removing it will cause other problems .

Install the configuration editor below if not already and look for check boxes for the items to be removed . I didn't see any .   ```
sudo apt-get install dconf-tools
```

---

### Post by jose lourenco on 2011-11-18
hi again

i looked into gconf and solved the problem

there were some options on what actions to do when pressing suspend/hibernate/power keys

i changed all that said "suspend" to "hibernate", this resulted in making the menu entry execute hibernate-disk instead of hibernate-ram

thanks a lot.

---

