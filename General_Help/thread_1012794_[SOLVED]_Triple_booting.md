---
title: "[SOLVED] Triple booting?"
date: 2008-12-16
forum: General Help
---

### Post by turgidtoupee on 2008-12-16
Currently I'm dual booting Vista and XP. If I were to use wubi to install ubuntu, could I get all three onto one boot menu (right now the vista one comes up), so that I get vista, xp and ubuntu on the same menu? Also, if I was to uninstall ubuntu would it take away the whole menu and make my xp install unusable?

The answers are probably obvious, but I've had bad experiences in the past with boot menus and have lost whole operating systems because of it. Any help would be much appreciated, as I'm anxious to get back to ubuntu, but have become somewhat paranoid about losing all the games I have installed on my vista and xp installs.
Thanks!

---

### Post by caljohnsmith on 2008-12-16
> **turgidtoupee said:**
> Currently I'm dual booting Vista and XP. If I were to use wubi to install ubuntu, could I get all three onto one boot menu (right now the vista one comes up), so that I get vista, xp and ubuntu on the same menu? Also, if I was to uninstall ubuntu would it take away the whole menu and make my xp install unusable?

If you install Ubuntu via Wubi to your Vista partition, that would be the most ideal, because then Ubuntu should be added to your current Vista boot menu as you want. If you install Ubuntu to the XP partition, Ubuntu will add itself to the XP boot loader, which might result in having to go through two boot screens to boot Ubuntu: in the first boot menu screen where you have Vista and XP listed, you would have to choose XP, and then a second boot screen would come up asking you to choose between XP and Ubuntu. Or if you still want to install Ubuntu to your XP partition, you could go through some trouble to manually add it to your Vista boot menu instead of the XP boot menu.

Also, when you go to uninstall Ubuntu, it shouldn't make either Vista or XP unusable; about the worst thing that happens is sometimes Ubuntu doesn't remove its boot entry from the Vista/XP boot menu, and then you have to manually do it. Anyway, good luck and let me know how it goes. :)

---

### Post by turgidtoupee on 2008-12-18
Worked perfectly. Got three entries in the boot menu, XP, Vista and Ubuntu, and ubuntu works just like it would if I'd given it it's own partition. Thankyou very much!

---

### Post by caljohnsmith on 2008-12-18
Glad to hear everything went smoothly with your Wubi install; cheers and have fun with Ubuntu. :)

---

