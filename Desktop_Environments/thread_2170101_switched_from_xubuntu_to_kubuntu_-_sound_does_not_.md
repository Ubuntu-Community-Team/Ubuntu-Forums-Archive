---
title: "switched from xubuntu to kubuntu - sound does not play through headphones"
date: 2013-08-24
forum: Desktop Environments
---

### Post by AENHYQp on 2013-08-24
i had xubuntu installed (13.*). after seeing the merits of  KDE's simplified answer to compiz, i installed kubuntu-desktop and logged into it and began setting it  up. now that i'm using KDE, sound does not play through headphones, but  instead plays through the laptop speakers (toshiba satellite c875). it was  working fine under xfce.

 i see the option in phonon under "audio  hardware setup" to switch "device configuration" from "speakers" to  "headphones", but when i change it, all the sound just STOPS. i've  rebooted after installing kubuntu-desktop, and after the sound didn't  work and i changed that setting, i logged out and back in. it still does  not work.

 any help would be appreciated - thanks in advance.

---

### Post by bra|10n on 2013-08-24
Systemsettings > Multimedia > Device Preference.
If you have multiple devices listed, is your preferred* device listed at the top of the list.

You can use the various test buttons to check for working devices.

---

### Post by AENHYQp on 2013-08-25
thanks, but i got it working (unintentionally). after another reboot, when i opened the sound manager, KDE told me it didn't think that a lot of settings/devices in its records were necessary. it asked me to disgregard their configs / delete them. i hesitantly agreed, and noticed no difference. after another reboot, sound works fine, so far :D.

man, i gotta say, i can't believe how far KDE has come. the last few years i've been wrestling with getting compiz running on gnome, then on xfce, etc... i wish i'd have accidently seen a video of KDEs cube effect sooner: it would have saved me a lot of hassles :D.

---

### Post by bra|10n on 2013-08-25
Good news.

I expect what KDE has done is eliminate the device profiles that it detected weren't working.

[quote=AENHYQp]...i wish i'd have accidently seen a video of KDEs cube effect sooner...[/quote]
Haha... you might not have appreciated it as much otherwise.

---

