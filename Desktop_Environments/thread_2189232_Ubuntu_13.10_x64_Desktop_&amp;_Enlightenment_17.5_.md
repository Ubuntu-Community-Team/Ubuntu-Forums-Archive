---
title: "Ubuntu 13.10 x64 Desktop &amp; Enlightenment 17.5 - No Applications/Files"
date: 2013-11-21
forum: Desktop Environments
---

### Post by oxsyn on 2013-11-21
I just did a fresh install of Ubuntu 13.10 x64 Desktop with full disk encryption & LVM.
I updated/upgraded the system and immediately installed enlightenment using the following steps:

```
sudo add-apt-repository ppa:efl/trunk
sudo apt-get update
sudo apt-get install e17 e17-data terminology
```

I cannot install e17-dbg, it appears that the package is not compatible with the efl ppa.

I rebooted the system, logged in with Enlightenment - no customization.

The "applications" menu is completely empty - nothing is being detected.  When I go to "Navigate -> Home -> {Desktop,Documents,Downloads,Music,Pictures,Public,Templates}" all folders show "No Listable Items".  I created some items in those folders to test, and they still do not show up.

Any idea what's going on and how I might fix it?  I haven't been able to find any answers or anyone else with this problem.

---

### Post by Frogs Hair on 2013-11-21
Hello

You can't mix E17 packages from the Ubuntu repository with that or any ppa which includes newer packages. The result is usually a broken package system. To start with a new E17 configuration open nautilus and delete the .e folder from hidden folders and the next time you login to E17 a new clean profile folder will be crated. This will solve any problems related to a corrupt profile. I have not tried E17 on 13.10 yet and I see your using  ppa that has 13.10 packages. There is always risk of problems with any ppa even if it is considered stable.

---

