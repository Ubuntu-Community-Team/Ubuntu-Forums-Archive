---
title: "Plz Help - bootup stalls after installing kubuntu-desktop"
date: 2006-11-07
forum: Desktop Environments
---

### Post by lodp on 2006-11-07
I installed kubuntu-desktop yesterday, and selected kdm as the default display manager (I did so in the dialogue that popped up, as well as, before that, manually in the file /etc/X11/default-display-manager). I usually don't power-down my system, so everything seemed to work fine at first.

Anyway, when I had to do a restart today, bootup stalls when there's about 1/3 of the progress bar completed underneath the kubuntu-logo. After some time, there's some blue distorted line popping up under the progress bar, then a green one, but then it's over.


Any ideas?

I'm pretty sure booting up DID work at least once yesterday, with kubuntu already installed. I'll try to switch back to gdm for a login manager, and see if that works. would prefer kdm, though.

---

### Post by michux on 2006-11-07
> **lodp said:**
> I installed kubuntu-desktop yesterday, and selected kdm as the default display manager (I did so in the dialogue that popped up, as well as, before that, manually in the file /etc/X11/default-display-manager). I usually don't power-down my system, so everything seemed to work fine at first.

Anyway, when I had to do a restart today, bootup stalls when there's about 1/3 of the progress bar completed underneath the kubuntu-logo. After some time, there's some blue distorted line popping up under the progress bar, then a green one, but then it's over.

I'm pretty sure booting up DID work at least once yesterday, with kubuntu already installed. I'll try to switch back to gdm for a login manager, and see if that works. would prefer kdm, though.

I don't think it's a kdm/gdm thing. It looks more like an X-Window-System issue. Perhaph you have installed NVidia drivers or tweaked the /etc/X11/xorg.conf file in some other way?

Doing the ```
dpkg-reconfigure xserver-xorg
``` from the command line could fix the problem in this case.

---

### Post by lodp on 2006-11-11
thanks -- i switched the default display manager back to gdm, and it works now (although curiously there's still the kubuntu-banner on startup). don't know what the issue was in the end (i've got proprietary ATI drivers running, but those had been in place before).

---

