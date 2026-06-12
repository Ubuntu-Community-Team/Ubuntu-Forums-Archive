---
title: "Why Bionic is deleting my old wallpaper sets?"
date: 2018-05-03
forum: Desktop Environments
---

### Post by marciomj on 2018-05-03
Not the end of the world, but I'm wondering why Bionic upgrade process is erasing my old wallpaper sets (dating since Xenial).

This happened in a bare metal machine, and also in a VM, both being upgraded since 16.04.

[ATTACH=CONFIG]279553[/ATTACH]

---

### Post by monkeybrain20122 on 2018-05-03
This is normal if you store your wallpaper in /usr/share/backgrounds because "upgrade" reverts system level to the standard configuration and erases all your customizations (if it works).  If you stored them in your home (~/Pictures, say) then they won't be erased.

---

### Post by marciomj on 2018-05-04
Thanks for the reply, monkeybrain20122.

I never changed the default wallpapers location.

What intrigued me is that this both installs have been upgraded since 16.04, and in the previous upgrades, the wallpaper set from the previous version was maintained.

Anyway, as I've said before, it isn't the end of the world. Just technical curiosity.

---

