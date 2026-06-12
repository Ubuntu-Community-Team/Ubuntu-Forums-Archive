---
title: "Google Chrome files."
date: 2011-04-16
forum: Desktop Environments
---

### Post by abiss27 on 2011-04-16
Hey guys, I uninstalled Google Chrome from my Ubuntu 10.10 system, I messed up one of the settings on the Browser itself can could not undo it, so I uninstalled it and reinstalled thinking that would work, but somehow the same settings and themes were applied to the Browser again, is there a folder where Google Chrome files remain on the system and if so where?

---

### Post by Copper Bezel on 2011-04-16
Removing a program does not, by default, remove its configuration files. Instead, use "apt-get purge" from the command line or select "completely remove" in Synaptic.

Chrome's settings are stored in your home directory under the hidden .config/google-chrome.

---

### Post by ~!geek!~ on 2011-04-16
> **Copper Bezel said:**
> Removing a program does not, by default, remove its configuration files. Instead, use "apt-get purge" from the command line or select "completely remove" in Synaptic.

Chrome's settings are stored in your home directory under the hidden .config/google-chrome.

Exactly..
Just remove the relevant folder from your home directory (use ctrl+h to view hidden directories having configurations ) You can remove or move it to some other place say your desktop (to act as a backup in case,  you want something back from old settings.) No need to reinstall your software (generally). Restart your software and you are done.. 
Hope it helps!!

---

