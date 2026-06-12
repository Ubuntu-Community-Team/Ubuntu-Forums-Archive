---
title: "Themeing not applied to applications Ubuntu Gome 14.04"
date: 2014-10-15
forum: Desktop Environments
---

### Post by TheTechnoViking on 2014-10-15
Hello,

Did a quick search and not many results if I am searching for the right criteria as I'm sure this will have been answered before. I have the Faience theme applied to the system, however, app's like synaptic package manager, keepassx etc does not have the theme applied.

If i'm on the right track this may "I think" be because one is gtk2.0 the other 3.0? Adwaita applies to everything obviously, but, like said themes don't.

A point in the right direction is greatly appreciated before I start hacking away at theme files, and, probably causing havoc no doubt.

Many Thanks

---

### Post by Frogs Hair on 2014-10-15
Hello and Welcome

Synaptic is opened with sudo in order to make changes to the package system and unless the themes are installed in usr/share/themes they won't be displayed in that application. I don't use Keepassx, but suspect the same is true.Themes stored in home .themes aren't visible in applications that require elevated permissions.

---

### Post by TheTechnoViking on 2014-10-15
Thank you for the response.

The theme's are now even stranger, i've copied them to /usr/share/themes nothing was showing in the advanced tweak tool, I opened this up with sudo gnome-tweak-tool and the theme appeared, set it up on the root account, elevated the file permissions in ~/.themes so I could get write access and set it up there as it then appeared, however still the same results, absolutely baffled! haha

Any ideas?

Thanks again

---

### Post by TheTechnoViking on 2014-10-15
All sorted now, I removed the ~/.themes folder and at last they appeared. There must have been some confusion.

Thank you again.

---

