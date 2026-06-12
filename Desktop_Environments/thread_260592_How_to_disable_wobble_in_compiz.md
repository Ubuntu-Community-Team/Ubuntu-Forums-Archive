---
title: "How to disable wobble in compiz?"
date: 2006-09-19
forum: Desktop Environments
---

### Post by MaXiMuS-D on 2006-09-19
Need help with that. Even if I deselect the plugin in csm, nothing happens. I've even tried killing compiz and restarting. I still get wobbly windows and menus. This is not JUST the wobbly effect, the same happens with every other setting too. The changes never take effect.

I just want to make the menus fade in, that's it....nothing more. No wobbly stuff, it makes me ill.

Just tell me which configuration files to edit......I don't like the looks of this settings manager, it's not usable enough yet...seems to have bugs.

Any help will be appreciated. Thx.

---

### Post by ButteBlues on 2006-09-19
> **MaXiMuS-D said:**
> Need help with that. Even if I deselect the plugin in csm, nothing happens. I've even tried killing compiz and restarting. I still get wobbly windows and menus. This is not JUST the wobbly effect, the same happens with every other setting too. The changes never take effect.

I just want to make the menus fade in, that's it....nothing more. No wobbly stuff, it makes me ill.

Just tell me which configuration files to edit......I don't like the looks of this settings manager, it's not usable enough yet...seems to have bugs.

Any help will be appreciated. Thx.
$ sudo chmod 755 ~/.compiz -R

Then change your settings in csm.

---

### Post by MaXiMuS-D on 2006-09-19
No such file exists!

But, for example, I go to csm and uncheck the wobbly plugin and quit it, no changes take effect. BUT when I again start csm, it tells me that the plugin has been disabled!

Isn't there a config. file I can just edit?

---

### Post by MaXiMuS-D on 2006-09-19
Okay, I finally did it through gconf-editor. Just disabled the "wobble on move" and removed the effect from "menu" and "unknown".

---

### Post by MaXiMuS-D on 2006-09-19
Oh, and you can also modify the script you created (see the ubuntuguide.org tutorial) and remove the wobbly plugin from there.

---

### Post by ButteBlues on 2006-09-21
Maximus - If editing gconf values worked, you're either: (a) using a deprecated way to start compiz, or (b) not using compiz-quinn.

---

### Post by Rashid584 on 2006-09-21
What if we use KDE and don't have gconf edit?

CSM works fine for me in everything, except disabling wobbly menus...

I don't think its a bug. CSM just confuses me. I dunno how to use it. Its not user friendly enough IMO :(

-Rashid

---

### Post by mariux on 2006-09-21
I think you have to restart X

---

### Post by MaXiMuS-D on 2006-09-22
> **a simple façade said:**
> Maximus - If editing gconf values worked, you're either: (a) using a deprecated way to start compiz, or (b) not using compiz-quinn.

Yes, I figured that out. It was changing the script that removed the wobbly effect.

---

