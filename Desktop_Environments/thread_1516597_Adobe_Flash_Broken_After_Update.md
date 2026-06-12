---
title: "Adobe Flash Broken After Update"
date: 2010-06-23
forum: Desktop Environments
---

### Post by Cerin on 2010-06-23
I just installed a bunch of updates, and found Adobe Flash was suddenly broken. Both Chrome and Firefox report a missing plugin, even though Flash had been working perfectly with the flashplugin-nonfree package installed. So I uninstalled this package, and tried to manually download and install the package from Adobe's site, only to find they only offer 32-bit binaries, which appear to be incompatible with my 64-bit system.

Has anyone else run into this problem? Why would an update suddenly break this functionality? How can I repair it?

---

### Post by lovinglinux on 2010-06-24
Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by 3Miro on 2010-06-24
Try removing the 32-bit flash player that you have installed and reinstall the "flashplugin-nonfree" package from Synaptic (System -> Admin -> Synaptic).

(to remove the 32-bit flash player, you should look into .mozilla (hit Ctr+H to see hidden files in the file manager) then remove the flashplugin.so file form plugins subfolder).

---

### Post by lovinglinux on 2010-06-24
> **3Miro said:**
> Try removing the 32-bit flash player that you have installed and reinstall the "flashplugin-nonfree" package from Synaptic (System -> Admin -> Synaptic).

(to remove the 32-bit flash player, you should look into .mozilla (hit Ctr+H to see hidden files in the file manager) then remove the flashplugin.so file form plugins subfolder).

FLASH-AID does that and also remove other plugins.

---

