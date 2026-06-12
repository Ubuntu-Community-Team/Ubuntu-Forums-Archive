---
title: "Getting Adept to un-greyout programs I want"
date: 2006-07-24
forum: Desktop Environments
---

### Post by shultzjr on 2006-07-24
When I go into add/remove programs and change from kde only to any suite and then check unsupported and proprietary, lots of programs show up but they are grayed out.  How do I get to a state where I can install them?

thanks....

---

### Post by mlind on 2006-07-24
Do you have multiverse and universe repositories enabled? Adept is bit scary, I've used aptitude's gui too, but it's much worse.

Synaptic is program to get overview about what's on the repositories.

---

### Post by shultzjr on 2006-07-24
Do you have multiverse and universe repositories enabled? Adept is bit scary, I've used aptitude's gui too, but it's much worse.
Synaptic is program to get overview about what's on the repositories

========================================================================

I edited the /etc/apt/sources.list file to enable all the repositories but when I go into Adept they are still grayed out.  I can't add Synaptic or anything that is not in the default install for Kubuntu.

any other suggestions?

---

### Post by shultzjr on 2006-07-24
And I did restart the computer.

---

### Post by mlind on 2006-07-24
> **shultzjr said:**
> 
I edited the /etc/apt/sources.list file to enable all the repositories but when I go into Adept they are still grayed out.  I can't add Synaptic or anything that is not in the default install for Kubuntu.

any other suggestions?

I'm not familiar with adept, but after you added new repositories you need to update the package lists. From command line it's *sudo aptitude update*, I guess *sudo adept update* may work too.

---

