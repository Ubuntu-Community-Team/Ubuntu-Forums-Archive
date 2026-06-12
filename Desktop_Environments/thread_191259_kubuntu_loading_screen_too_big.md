---
title: "kubuntu loading screen too big"
date: 2006-06-07
forum: Desktop Environments
---

### Post by smokey_ketchup on 2006-06-07
Hi 

I recently freshly installed Kubuntu 6.06 onto my desktop. The install was fine, but when I reboot or shutdown the loading screen, the one with the big kubuntu logo and the loading/unloading messages, appears too big for the screen size. This means that the current message (e.g. configuring network interfaces...) appears to be off the bottom of the screen, therefore I cannot tell if something has gone wrong or taking a long time to load/unload.

This was not a problem in Kubuntu 5.10

How can I configure this screen?


Thanks

---

### Post by D!mon on 2006-06-11
[QUOTE=smokey_ketchup]Hi 

I recently freshly installed Kubuntu 6.06 onto my desktop. The install was fine, but when I reboot or shutdown the loading screen, the one with the big kubuntu logo and the loading/unloading messages, appears too big for the screen size. This means that the current message (e.g. configuring network interfaces...) appears to be off the bottom of the screen, therefore I cannot tell if something has gone wrong or taking a long time to load/unload.

This was not a problem in Kubuntu 5.10

How can I configure this screen?


Thanks[/QUOTE]

I had the same problem but only with login window: it was too big and refresh rate was swt to 60Hz. Actually I don't know what the right solution is, but I commented out all modes which I don't use at the xorg.conf file (e.g. modes with low refresh rate or big resolution) and that resolved problem for me

---

### Post by wootah on 2008-05-22
For review's sake, the answer is posted [here]("http://ubuntuforums.org/showpost.php?p=5020690&postcount=3") on [this thread]("http://ubuntuforums.org/showthread.php?p=5020690#post5020690").

---

