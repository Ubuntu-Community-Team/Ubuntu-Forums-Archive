---
title: "reopened applications at login?"
date: 2014-06-08
forum: Desktop Environments
---

### Post by juju43 on 2014-06-08
Hello,

is there any way with lubuntu (12.04 or 14.04) to restore previously opened applications at login? if possible same dimension/position.

I found this for ubuntu
[http://en.kioskea.net/faq/15528-ubuntu-automatically-restore-last-opened-programs-at-next-sessi](http://en.kioskea.net/faq/15528-ubuntu-automatically-restore-last-opened-programs-at-next-sessi)
on lubuntu, there is only preferences: session settings but it doesn't allow to customize all apps, just registered one like dropbox, ssh agent ...

Thanks

---

### Post by vasa1 on 2014-06-08
> **juju43 said:**
> ...
is there any way with lubuntu (12.04 or 14.04) to restore previously opened applications at login? if possible same dimension/position.
...
Lubuntu has less features than many other distros. AFAICT, this is by design.

If you want certain applications to always open at login, you'll need to put them in your autostart file. The procedure has changed between 12.04 and 14.04. I don't think Lubuntu has the feature of opening applications left open in the last session. Xubuntu might have that.

Re. same dimension/position, you'll need to look at ~/.config/openbox/lubuntu-rc.xml.

---

### Post by amanchesterman on 2014-06-09
*Xubuntu might have that.*

Yes. In Xubuntu 14.04 it's at Settings > Session and Startup > Logout Settings > Automatically save session on logout

---

### Post by juju43 on 2014-06-11
Yeah. no native option. a pity

I'll try to work it out with Autostart and some one-command tiling.

maybe with [http://ubuntuforums.org/showthread.php?t=2078867](http://ubuntuforums.org/showthread.php?t=2078867)
or
[http://www.giuspen.com/x-tile/](http://www.giuspen.com/x-tile/)

---

