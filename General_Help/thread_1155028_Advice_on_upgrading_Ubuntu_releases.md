---
title: "Advice on upgrading Ubuntu releases"
date: 2009-05-10
forum: General Help
---

### Post by Andy06 on 2009-05-10
So I usually install the newest release for myself as well as at least 15-12 other comps (frs, family, acquaintances).

Thing is, with a 6 month release cycle, it gets very tiring very soon. Upgrading is not an option since it breaks too many things, too many driver/kernel issues and general mayhem (not on every computer, but enough for it to be an issue). Also the separate home partition method doesn't really work for programs settings since versions get upgraded and it just doesn't work perfectly like it should. [The actual use files and data such as Documents, Pictures, Music and Videos are on a completely separate partition and not an issue]

So ultimately, I have to do clean installs with every new version, then customise the panels , settings for all the preferences in the control panel [preferences + system administration], theme customising and THEN load all the 20+ apps, icon packages, back end packages etc etc

Does anyone have any advice on a better way (I'm sure there is), is there a way to automate all of this? I know there is remastersys for Live USBs, but what about full installs?

Upgrading is also not an option when a new version brings significant updates. (such as ext4 in 9.04 and the new themework hopefully coming in 9.10).

Thanks a lot

---

### Post by 4Orbs on 2009-05-10
Downloading all the different packages for apps, icons, themes is the most time consuming part of the process. But if you use aptoncd (Apt on CD) you need to download these things only once for any given distribution release. Then make iso's or CD's containing all those apps and quickly restore the packages to any new installation's apt-cache. Icons, themes and wallpapers can be stored in a folder and burnt to CD without using aptoncd.

---

### Post by Andy06 on 2009-05-10
Yeah I now use an external USB for wallpapers, icons and themes.

But apps, programs, settings, screenlets, compiz and cairo configuration are still a pain. I just wish upgrading was a seamless, perfect experience like it sounds! Unfortunately it always breaks something. And the separate home partitions leaves me midway between a clean and unclean install with some of the problems of unclean upgrades without the "clean slate" feeling of a fresh install.

---

### Post by colau on 2009-05-10
> **4Orbs said:**
> Downloading all the different packages for apps, icons, themes is the most time consuming part of the process. But if you use aptoncd (Apt on CD) you need to download these things only once for any given distribution release. Then make iso's or CD's containing all those apps and quickly restore the packages to any new installation's apt-cache. Icons, themes and wallpapers can be stored in a folder and burnt to CD without using aptoncd.
Hi,
+1 for 40rbs.
Would you please tell why is the aptoncd showing 6 packages by default to create the iso?

---

### Post by 4Orbs on 2009-05-10
I don't know if this will apply to your situation, but when I upgrade:

1. Turn off desktop effects, switch to the default theme (Human)
2. Set the screen resolution (as root) back to default or auto (even if it's ugly)
3. Deactivate the graphics driver (nVidia Legacy in my case)
4. Upgrade
5. Activate the graphics driver
6. Set the resolution (as root) to my preferred
7. Customize

My upgrade from 8.10 to 9.04 went smoothly following those steps.

---

### Post by 4Orbs on 2009-05-10
> Would you please tell why is the aptoncd showing 6 packages by default to create the iso?

A new Ubuntu installation will have an empty apt-cache because all the apps were installed from the cd. But after you install the updates, those packages (the update packages only) will be in the cache. Any new apps you install afterwards will also be in the cache. If you run sudo apt-get clean, then you will empty the cache and require re-downloading those packages (if you want to put them on a cd using aptoncd).

---

### Post by colau on 2009-05-10
> **4Orbs said:**
> A new Ubuntu installation will have an empty apt-cache because all the apps were installed from the cd. But after you install the updates, those packages (the update packages only) will be in the cache. Any new apps you install afterwards will also be in the cache. If you run sudo apt-get clean, then you will empty the cache and require re-downloading those packages (if you want to put them on a cd using aptoncd).
Thanks 40rbs.

---

### Post by Neostar on 2009-05-10
You don't always have to upgrade to a new version just use the long term support versions. They get security updates for 3 years and you would only need to upgrade once every 3 years.

---

### Post by Andy06 on 2009-05-10
But then you wouldn't get all of the latest and greatest stuff.

---

