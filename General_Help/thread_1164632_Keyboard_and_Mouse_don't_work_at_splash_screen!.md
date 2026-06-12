---
title: "Keyboard and Mouse don't work at splash screen!"
date: 2009-05-19
forum: General Help
---

### Post by Garofoli on 2009-05-19
Hey [Ubuntu],
Something is terribly wrong with my Ubuntu. The last time before I restarted my computer was when I installed Steam in wine. Last week I deleted the whole /var/cache folder for disk space reasons (No flame, please). I can use the keyboard in Bios and in the root console but I can't log into the splash screen. Any ideas? Thank you.

BTW: Reposting it here because Dell Support gets no views.:p

---

### Post by coffeeaddict22 on 2009-05-21
Umm, it sounds like you know what the problem might be.  Have a look [here]("http://www.pathname.com/fhs/pub/fhs-2.3.html#THEVARHIERARCHY") at what you might be missing.  The doc states explicitly the application must be able to recover from deletion of a /var/cache/ file, but I'd guess from your description you trashed your graphical display manager.  
Options: the quick one would be either ```
xfix
``` in your root terminal, or the "repair my graphics" option in the recovery console; otherwise, easiest would be a reinstall.

---

