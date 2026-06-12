---
title: "Will UNR upgrade rather than overwrite 8.10?"
date: 2009-04-24
forum: General Help
---

### Post by Felipejane on 2009-04-24
I bought my Asus EeePC 1000H with Windows XP on it, and successfully made it a dual-boot machine with Ubuntu 8.04, later upgrading that to 8.10. I have the UNR on a flash drive, like the way it looks, and want to **upgrade** rather than overwrite the existing installation. Will the netbook remix let me do that, or must I archive all my data and replace 8.10 with the 9.04 netbook remix?

---

### Post by sflory on 2009-04-24
It might be easier to just upgrade to the current release.
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

Then fire up synaptic (**System** > **Administration** > **Synaptic Package Manager**) , search for "remix", install those packages, install desktop-switcher, and netbook-launcher.  Then  use the switching tool (**System** > **Preferences** > **Switch Desktop Mode)**

---

### Post by Felipejane on 2009-04-25
Well, that *almost* worked. And it certainly had the advantage of leaving the WinXP partition untouched, which was the primary goal. 

The only problem is that somehow the upgrade messed up the ability (under Linux) to grab hold of either the ethernet or the wireless connection. (Wireless was never reliable under 8.10, but the ethernet connection always worked.) This problem only became apparent when I went to download the items tagged "remix", as suggested; Synaptic Package Manager couldn't find the path to the repository. Likewise, I was unable to go to any sites using any browser.

I know the ethernet cable and wireless are both good, because I've used both successfully since performing the upgrade by booting in Windows. But I don't know enough about what parameters are set and where in Linux to make wireless and wired Internet connections viable. Any thoughts? I tried various combinations in WICD, but never could find one that worked.

---

