---
title: "Gnome-panel excessive memory usage"
date: 2012-08-16
forum: Desktop Environments
---

### Post by sonnet on 2012-08-16
I performed a minal command line installation with ubuntu-server 12.04 cd.
On top of that, later I installed gnome-shell and the applications I needed.
Among them, I installed libreoffice 3.6 from a PPA. The Libreoffice applications didn't get into the menu directly,
so I modified Alacarte options.
After doing that, gnome-panel memory usage spiked to 45-50mb while before was below 6mb.
I did the installation 2 times and 2 times I had the same problem.
Even after rebooting Gnome-panel keep using so much memory.
The menu also became lightly less responsive.

Does anybody have any idea about how can I fix this?

Edit : **[COLOR="Red"]installation of Libreoffice 3.6 is 100% the reason for such increase[/COLOR]**

---

### Post by sonnet on 2012-08-17
I made the installation 3 more times, to check what was wrong.
I tried it again to install directly from the ppa repository,
I tried it manually and I tried to upgrade to it from 3.5 release.
All the 3 attempts brought to the same result:
Libreoffice 3.6 installation brings the gnome-panel to increase the memory usage by roughly 40mb (from 6-7mb to 47mb).

Maybe this could be the package , it would be nice if anyone using a different DE that is not using gnome-panel and report if he got any similar increase in memory usage or someone using gnome-panel and libreoffice but with a different distribution than Ubuntu (better if not debian based I guess)

---

