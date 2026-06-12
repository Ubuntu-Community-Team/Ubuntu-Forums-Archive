---
title: "Removing ath5k Driver and Backport Modules"
date: 2009-04-06
forum: General Help
---

### Post by ftabor on 2009-04-06
I am running Intrepid on a HP Pavillion laptop using the ath5k driver and the Backport modules.  I'm going to get a supported wifi card and wish to remove the ath5k driver and remove the backport modules and revert back to the standard kernal.

Any advice on how to proceed with removing the ath5k driver and backport modules?

---

### Post by mikewhatever on 2009-04-06
You can blacklist ath5k in /etc/modprobe.d/blacklist, which should prevent it from loading. I'm not quite sure about the backport modules. Is uninstalling an option?

---

### Post by ftabor on 2009-04-06
Hmmm, looking back through my notes when I installed, yep, the backports were installed with apt-get, so I should be able to just uninstall, then update everything else.  

It was the ath5k driver that I was most concerned about, thanks.

---

