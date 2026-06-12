---
title: "Nautilua Stuck in Browser Mode"
date: 2007-06-16
forum: Desktop Environments
---

### Post by dshan on 2007-06-16
I recently upgraded my Dell laptop from 6.10 to 7.04, which went without apparent problems, but after lots of subsequent problems (various previously working programs hung and other weird stuff) I decided to do a complete new install of 7.04. 

That seems to have sorted out almost all the problems, however I now have a new issue that did not occur in 6.10 and I'm pretty sure did not happen when I initially upgraded to 7.04 from 6.10: Nautilus keeps using single window browser mode when I double-click on folders (or File>Open a selected folder) to open them, even though I don't have "Always open in browser windows" checked in File Management Preferences under the Behaviour tab. If I do a File>Open Parent in a folder window though it opens the parent in a separate window.

Anyone got any idea what's going on here? I hate browser mode...

Ah! Problem solved - I needed to check the "no_ubuntu_spatial" option in nautilus preferences using Config Editor as well as have "Always open in browser windows" unchecked. I guess "no" doesn't always mean no. Anyone know why?

---

