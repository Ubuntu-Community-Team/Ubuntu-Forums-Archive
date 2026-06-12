---
title: "compiz - restore defaults"
date: 2009-04-20
forum: General Help
---

### Post by robos85 on 2009-04-20
Hi, how can I restore default settigns via terminal?
I installed compiz, set some settings but then screen gone crazy:( I got bkack places instead of windows:/

Help please.

---

### Post by LoloftheRings on 2009-04-20
Remove compiz including config files:
```
sudo apt-get purge compiz*
```
See what packages are removed during uninstallation and reinstall these packages using
```
sudo apt-get install ...
```
replacing ... with all packages that were removed during the purge command.

Good luck

---

