---
title: "Ubuntu Unity 24.04 (beta) - Any experiences on upgrade / fresh install?"
date: 2024-04-21
forum: Desktop Environments
---

### Post by jauntyjackalope2 on 2024-04-21
hi all,

**does anybody has experiences on upgrading to ubuntu unity 24.04 from an 23..10 installation?**
to be honest, i don't even know the main differences between an upgrade or fresh install regarding this flavor.

i'm (test)installing the beta right now on an older acer aspire e1 - and although the installer finished with an error message saying the install failed, it boot's and is updating right now and looks not bad so far.
unfortunately the "official" unity forum is down since several month, that's why i'm trying to possibly get some community interaction in this thread.

thanks and have a great sunday, best, me (-:


edit: the fresh install of the beta on the aspire looks pretty stable, and, pretty performant as well (-: [https://ibb.co/Qfp8Ndn](https://ibb.co/Qfp8Ndn)
[IMG]https://ibb.co/Qfp8Ndn][img]https://i.ibb.co/qd70s59/1.png[/IMG]
[IMG]https://ibb.co/Qfp8Ndn[/IMG]
[IMG]https://app.gemoo.com/share/image-annotation/640609509397544960?codeId=vJ31jbZgozBmg&origin=imageurlgenerator&card=640609507401023488[/IMG]

---

### Post by Frogs Hair on 2024-04-21
24.04 is four days shy of release and I would expect an upgrade facilitated by the developer will be available soon like the other Ubuntu flavors. You can also wait until the 25th or when the the developers post a link to the final release.

---

### Post by guiverc on 2024-04-21
> **jauntyjackalope2 said:**
> 
**does anybody has experiences on upgrading to ubuntu unity 24.04 from an 23..10 installation?**
to be honest, i don't even know the main differences between an upgrade or fresh install regarding this flavor.
[IMG]https://ibb.co/Qfp8Ndn][img]https://i.ibb.co/qd70s59/1.png[/IMG]
[IMG]https://ibb.co/Qfp8Ndn[/IMG]
[IMG]https://app.gemoo.com/share/image-annotation/640609509397544960?codeId=vJ31jbZgozBmg&origin=imageurlgenerator&card=640609507401023488[/IMG]

No I don't have any experience.. but I'll still provide some thoughts.

- I've seen many reports of problems in the *release-upgrade* process, but the focus currently is on release of Ubuntu 24.04 LTS (*RC still hasn't been released*) where the ISO release is for NEW installs, not *release-upgrades*.

You can see status best via watching this page

 [https://discourse.ubuntu.com/t/noble-numbat-24-04-release-status-tracking/44043](https://discourse.ubuntu.com/t/noble-numbat-24-04-release-status-tracking/44043)

Where post-release of Ubuntu 24.04 LTS (*which includes all flavors such as Ubuntu Unity*) the focus will switch to *release-upgrades* from *mantic* or 23.10 first, and when that's considered *stable* a change to the [*meta file*]("https://changelogs.ubuntu.com/meta-release") will be made, as its only after this change that installed systems will detect the release of Ubuntu 24.04 LTS (*ie. ISO release won't installed systems, ISO is for new installs*).

The Ubuntu Release team usually meet early in the week to *discuss* the status of the *upgrade path* and decide if it's ready.. and then re-assess that until a decision is made it's *ready* and the meta file gets changed.  If people don't want to wait, they can always use [`-d` ]("https://changelogs.ubuntu.com/meta-release-development")which causes a different meta file to be used (*that option allows QA*).

***beta* ISO warning**

Please don't test the beta ISO if you're still doing install testing. The beta is a *daily* ISO that is just named the *beta* as its a key milestone, and the production of *daily *ISOs is paused for the weekend... after which they restart up & thus the *beta* ISO is now very old.  If however you've installed the system & performed normal upgrades; you're system is very close to RC status & far from what was released as *beta* now.

If you discover bugs, please file them. 

 [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

***release-upgrade* versus *install***

What release you install with sets many defaults... With *flavors* the ISO of 22.04 will dictate if you're using a GA or HWE kernel stack for example (22.04 & 22.04.1 ISOs install the GA stack for Ubuntu Unity, 22.04.2 & later install the HWE stack)...  as example, so if you *release-upgrade* that default will continue into the next release... (*even if the newer release changed the default behavior)... *ie. a *release-upgrade* will make the minimal changes to your system required to get to the next system.

If you clean install a new release, you'll have all the behaviors of the new release, and none of the prior defaults/behaviors will be present.. It may thus feel a *newer* system as it'll have more differences than a *release-upgrade* where many *behaviors* remained unchanged.

I've used the kernel stack as an easy example... (eg. if your install was 22.04.3 media you installed the HWE kernel stack.. if you *release-upgrade to 24.04 you'll remain on HWE.. however a clean install of 24.04 will install the GA kernel stack for Ubuntu Unity.. a difference you may not notice at first.. but you will over time*), but there are many changes that occur over time, including file-system permissions & more.

Most users will probably not notice these differences though... happy only when their system works.

---

### Post by jauntyjackalope2 on 2024-04-24
thank you very much for your replies! guiverc, especially for the material, knowledge and posted links! i'm coming back to this with a bit more time, to be able to respond adequately.

best, me (-:

p.s. i didn't find a possibility to somehow "vote up"/value your contribution, otherwise id' have done so.

---

