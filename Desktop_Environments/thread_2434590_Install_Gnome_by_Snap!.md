---
title: "Install Gnome by Snap?!"
date: 2020-01-08
forum: Desktop Environments
---

### Post by shmu26 on 2020-01-08
I am running Kubuntu 19.10 and I am thinking about installing Gnome.
I saw it offered as a snap.
[https://snapcraft.io/install/gnome-3-34-1804/kubuntu](https://snapcraft.io/install/gnome-3-34-1804/kubuntu)
What is this package?

---

### Post by Holger_Gehrke on 2020-01-08
As the description says: base libraries and desktop integration. It's a helper package for Gnome based programs packaged as snap so they don't have to either bring along 100 MB+ in libraries each of them. This package does AFAIK not contain a desktop you could use.

Holger

---

### Post by Dennis N on 2020-01-08
That is just a support package for gnome applications. You can see it in a list of installed snaps:

```
dmn@Sydney-VM:~$ snap list
Name                  Version                     Rev   Tracking  Publisher   Notes
atari800-jz           3.1.0-0                     1     stable    jz          -
chromium              79.0.3945.79                971   stable    canonical&#10003;  -
core                  16-2.42.5                   8268  stable    canonical&#10003;  core
core18                20191212                    1288  stable    canonical&#10003;  base
firefox               71.0-5                      287   stable    mozilla&#10003;    -
gnome-3-26-1604       3.26.0.20191114             98    stable/…  canonical&#10003;  -
gnome-3-28-1804       3.28.0-16-g27c9498.27c9498  110   stable    canonical&#10003;  -
gnome-calculator      3.34.1+git1.d34dc842        544   stable/…  canonical&#10003;  -
gnome-characters      v3.32.1+git3.b9120df        375   stable/…  canonical&#10003;  -
gnome-logs            3.34.0                      81    stable/…  canonical&#10003;  -
gnome-system-monitor  3.32.1-3-g0ea89b4922        123   stable/…  canonical&#10003;  -
gtk-common-themes     0.1-25-gcc83164             1353  stable/…  canonical&#10003;  -
quadrapassel          3.32.0+git3.1c047df         175   stable    canonical&#10003;  -
snap-store            20191114.a9948d5            209   stable    canonical&#10003;  -

```

---

