---
title: "distorted icons on panel and desktop"
date: 2010-04-22
forum: Desktop Environments
---

### Post by ZombieApocalypse on 2010-04-22
After upgrading from Kubuntu 9.04 to 9.10, I occasionally (though increasingly frequently), experience the problem of distorted icons on the panel and desktop. All other icons, menus and graphics (at least that I am aware of) appear fine and functional. I tried upgrading to KDE 4.4.2, but this did not remedy the issue. 

Once the distortion occurs, it is not resolved by rebooting. Interestingly though, it is temporarily remedied by uninstalling something from the package manager - therefore I simply install then immediately uninstall a package for a temporary fix.

Any suggestions?

---

### Post by shaka_zulu on 2010-04-22
That is why i am always performing clean install. Upgrading in Ubuntu or Kubuntu is now always easy and smooth job. This kind of inconsistencies always proof that. After that kind of problems i only loose my nerves and reinstall whole system. :)

---

### Post by ZombieApocalypse on 2010-04-22
I tried a clean reinstall from the CD, but the problem remains. Whenever I have problems after upgrading, I usually end up doing a clean install. It's often the best solution.

---

### Post by shaka_zulu on 2010-04-22
Write what graphic card you have, drivers verision, 32bit or 64bit OS?

---

### Post by ZombieApocalypse on 2010-04-22
I'm running it on an upgraded HP xe4500 laptop. 

_**Basic specs:**_
  **CPU:** Intel Pentium 4-M 1.7 GHz (32bit)
**Mem:** 768MB DDR SDRAM PC2100
**HD:** 80GB Toshiba (not of the model)
**GFX:** ATI Mobility M6; AGP 4x; 32MB DDR SDRAM; 24-bit colour support
**Display:** 1024x768 (XGA)

My xorg.conf file is configured for the ATI driver. Much of the display is corrupt using the vesa driver. Also, the display corrupts if acceleration is not set to EXA.

---

### Post by ZombieApocalypse on 2010-04-22
Also, prior to version 9.10, I was able to run the display perfectly using the vesa driver.

---

### Post by ZombieApocalypse on 2010-04-22
I solved the problem by deleting the icon cache and rebooting ie:

rm /var/tmp/kdecache-$USER/kpc/kde-icon-cache.*

---

