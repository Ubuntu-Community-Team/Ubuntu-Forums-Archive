---
title: "Kubuntu crashes 10.10 - windows decorator"
date: 2011-03-09
forum: Desktop Environments
---

### Post by nicolasdiogo on 2011-03-09
Hi follow Ubuntu users,

I have always used ubuntu (gnome) desktop – but recently I decided to try Kubuntu (kde).

It has been many years since I last used KDE.  And I decided to install it on my laptop; thus running KDE and Gnome side-by-side on a 10.10 x64 installation.

I have noticed that KDE looks really slick and that it still is massively more complicate compared to Gnome, this complication does allow for more customisation.

But I am facing some problems particularly with stability.

Every time I boot into KDE, it crashes complaining about window decorations.  I am using a T410 lenovo.

Any suggestions on how to fix these problems?

please see attached crash report from KDE.

thanks,


Nicolas

---

### Post by Lucradia on 2011-03-09
Are your graphics the NVS3100M (Nvidia) or the Intel?

Either way, it seems you might want to turn off compositing if it's on in KDE.

---

### Post by nicolasdiogo on 2011-03-09
Nvidia card with current driver which works fine on gnome.

would that be causing the problem?

the bit i am puzzled is that at start up window decoration crashes - but if run

```

kwin --replace

```

it works fine - it seems to fail only when i login.

---

