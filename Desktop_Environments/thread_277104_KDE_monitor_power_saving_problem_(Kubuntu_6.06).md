---
title: "KDE monitor power saving problem (Kubuntu 6.06)"
date: 2006-10-14
forum: Desktop Environments
---

### Post by kalahari875 on 2006-10-14
KDE's power saving feature never turns off my monitor, a ViewSonic E771. It does however detect my monitor properly (as a ViewSonic E771-4). In kcontrol | Peripherals | Display | Power Saving, I have checked "Enable Power Saving" with "Switch off monitor after" set to 15 minutes.

I know the monitor supports power saving in some fashion as Windows XP always turns off the monitor as specified.

Any ideas? This has been a problem regardless of the KDE version (from 3.5.2 to 3.5.5, applied today from kubuntu.org packages).

Thanks!

---

### Post by elettronicha on 2006-10-14
Might it be an issue related to conflicts with Kscreensaver settings? Did you try to disable the screensaver?

---

### Post by kalahari875 on 2006-10-14
I did try disabling the screensaver. At the appointed time, it does blank the screen, but the monitor remains on. Any ideas?

---

### Post by elettronicha on 2006-10-14
It seems a bug, isn't it? You made me notice that! I use Kubuntu Edgy and it has the same behavior with my Asus M6Ne laptop: screensaver disabled, but after the set delay KDE blanks the screen but doesn't turn it off.

I'll file it.

---

### Post by kalahari875 on 2006-10-14
Thanks! I was just getting on here to file it too. Here is some more information that you can include in the bug report (or I can add once you have it established):

If you add the following to the Monitor section in /etc/X11/xorg.conf it enables KDE to turn off the monitor:
[INDENT]option "DPMS" "true"[/INDENT]

However, from what I've read, KDE's power saving settings are supposed to override what we specify in xorg.conf.

One additional related problem I've noticed is that KDE forgets my settings for the power saving interval. I keep setting it to 15 minutes and applying, but upon rebooting, it stubbornly keeps returning to the default 25 minutes.

---

### Post by elettronicha on 2006-10-15
> **kalahari875 said:**
> Thanks! I was just getting on here to file it too. Here is some more information that you can include in the bug report
Sorry, unfortunately (or fortunately I'd say :D) with latest updates the screen is turned off correctly, so I can file the bug no more.

> One additional related problem I've noticed is that KDE forgets my settings for the power saving interval. I keep setting it to 15 minutes and applying, but upon rebooting, it stubbornly keeps returning to the default 25 minutes.
That is true and I'll file it right now, though the default is 5 hours to me.

---

### Post by elettronicha on 2006-10-15
> **kalahari875 said:**
> One additional related problem I've noticed is that KDE forgets my settings for the power saving interval. I keep setting it to 15 minutes and applying, but upon rebooting, it stubbornly keeps returning to the default 25 minutes.
Bug filed, you can add your comment if you want. bug #66215

---

