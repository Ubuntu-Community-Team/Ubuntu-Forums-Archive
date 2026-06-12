---
title: "KDE 4.3 only two virtual desktops when using Compiz Fusion."
date: 2010-01-04
forum: Desktop Environments
---

### Post by lightningfox on 2010-01-04
Hello

I am using Kubuntu 9.10 with KDE 4.3.

KDE's desktop effects aren't good enough, so I disabled them and I installed
Compiz fusion and all the KDE related Compiz fusion packages.

When I don't have Compiz enabled my taskbar has four virtual desktops, but when I have compiz enabled the four virtual desktops become two virtual desktops.


I tried manually making it four virtual desktops again by changing the number of virtual desktops from two to four in the Pager settings, but it doesn't work and it is still only two virtual desktops.


Please help me fix this.

---

### Post by roggenschrotbrot on 2010-01-05
if using compiz the number of virtual desktops has to be set with the general options tab of compizconfig-settings-manager (install it if you don't find it within 'system/settings').

---

### Post by 3Miro on 2010-01-05
As the user above said, you need compizconfig-setting-manager, you can install is via:
```
sudo apt-get install compizconfig-setting-manager

```

Then it will create ashortcut in one of the menus (in Gnome it is System -> Prefs, I am not sure about KDE). You can manage all effects from there.

I hope you know that compiz+KDE is less stable than kWin+KDE or compiz+Gnome.

---

