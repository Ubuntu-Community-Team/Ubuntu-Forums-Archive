---
title: "Kde Upgrade, Lost Wifi"
date: 2006-01-17
forum: General Help
---

### Post by lokirulez on 2006-01-17
I am currently running Kubuntu 5.10, everything was working great. I connect to the net via my Intel Pro Wireless 2200 card. Last night I upgraded to kde 3.5 with **apt-get dist-upgrade**. After the packages were downloaded and installed, rebooted. Everything seemed fine so I shutdown and went to sleep. Today when I logged in, I lost my wifi capabilities! I noticed that this upgrade installed a newer kernel, I had 2.6.12.9, I now have 2.6.12.10. I tried to re-install my ipw2200 drivers from source and got an error about /lib/modules/2.6.12.10-686/build not being found. There is a /lib/modules/2.6.12.10-686/ folder, but no build. I tried making a build folder within that directory but that did not change anything.  I guess I am trying to find out why this upgrade installed this new kernel (I thought I was just upgrading kde)? Why are my ipw2200 drivers not working? Also why did it not upgrade to the current kernel 2.6.15.1? Any suggestions would be appreciated.

---

