---
title: "Installation of KDE libraries slowdown Gnome boot?!?"
date: 2010-05-23
forum: Desktop Environments
---

### Post by dementic on 2010-05-23
Hello,

Here is what I saw. I have Ubuntu 10.04. I installed the KDE libraries to use Okular. Then Ubuntu took almost 30s more to boot (20s black screen between login and desktop). I uninstalled KDE, booted on another kernel, rebooted and the boot time was OK again (25s). 

I reinstalled KDE, 55s to boot again. Rebooted couples of times always the same. Rebooted on another kernel then again on mine (it seems to fix the slow boot times). 

Boot time was 35s (I thought it was OK). After lauching Okular, the boot time was again 55s... 

Removed KDE, Okular, and the boot time is normal again since 10 reboots....

WTF with KDE???

---

### Post by Zorael on 2010-05-23
It really depends on what was installed alongside Okular. It could be installing a whole lot more due to apt nowadays installing recommended packages by default.

```
$ sudo aptitude install okular --without-recommends
```
That should make it only install Okular and its dependencies, and ignore package recommendations.

If this doesn't help (or if you want a detailed view on what's actually being run at boot), you can try using bootchart to generate a graph of your boot process. That way you can identify what's causing your delays.

---

### Post by dementic on 2010-05-23
I think Okular needs KDE anyway but I would like to install KDE, the problem is that for an unknown reason it cause some delay when booting. I thought at bootchart but it's probably KDE since nothing else is installed. Another point is that I don't only need the dependancies for Okular but for Digicam aswell...

I would like to have some other advices of people who installed the package kubutu-desktop aside with ubuntu-desktop and the impact of the booting time.

---

