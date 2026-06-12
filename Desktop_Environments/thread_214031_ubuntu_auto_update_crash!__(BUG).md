---
title: "ubuntu auto update crash!  (BUG?)"
date: 2006-07-12
forum: Desktop Environments
---

### Post by quick on 2006-07-12
Hi :)

so you all know the orange ubuntu auto update button in the gnome notification area?
its a nice feature.

today it suggested updating the kernel and i clicked on the "show details" button it started downloading infos and then i got thrown back to gdm login screen.

i tried this 5 times! always back to gdm

just wanted to tell you guys


greets

---

### Post by Seaman on 2006-07-12
Make **sudo apt-get -s dist-upgrade** in the terminal and tell us which packages it tries to install (or just paste the output from the command).

---

### Post by quick on 2006-07-12
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade...Done
The following NEW packages will be installed
  linux-image-2.6.15-26-k7 linux-restricted-modules-2.6.15-26-k7
The following packages will be upgraded:
  linux-image-k7 linux-k7 linux-restricted-modules-common
  linux-restricted-modules-k7 nvidia-glx openoffice.org openoffice.org-base
  openoffice.org-calc openoffice.org-common openoffice.org-core
  openoffice.org-draw openoffice.org-evolution openoffice.org-gnome
  openoffice.org-gtk openoffice.org-impress openoffice.org-java-common
  openoffice.org-l10n-en-us openoffice.org-math openoffice.org-writer
  python-uno ttf-opensymbol
21 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Inst linux-image-2.6.15-26-k7 (2.6.15-26.44 Ubuntu:6.06/dapper-security)
Inst linux-image-k7 [2.6.15.23] (2.6.15.24 Ubuntu:6.06/dapper-security)
Inst linux-restricted-modules-common [2.6.15.11-2] (2.6.15.11-3 Ubuntu:6.06/dapper-security)
Inst linux-restricted-modules-2.6.15-26-k7 (2.6.15.11-3 Ubuntu:6.06/dapper-security)
Inst linux-restricted-modules-k7 [2.6.15.23] (2.6.15.24 Ubuntu:6.06/dapper-security)
Inst linux-k7 [2.6.15.23] (2.6.15.24 Ubuntu:6.06/dapper-security)
Inst nvidia-glx [1.0.8762+2.6.15.11-2] (1.0.8762+2.6.15.11-3 Ubuntu:6.06/dapper-security)
Inst openoffice.org-l10n-en-us [2.0.2-2ubuntu12] (2.0.2-2ubuntu12.1 Ubuntu:6.06/dapper-security)
Inst openoffice.org-common [2.0.2-2ubuntu12] (2.0.2-2ubuntu12.1 Ubuntu:6.06/dapper-security)
Inst ttf-opensymbol [2.0.2-2ubuntu12] (2.0.2-2ubuntu12.1 Ubuntu:6.06/dapper-security)
Inst openoffice.org-core [2.0.2-2ubuntu12] (2.0.2-2ubuntu12.1 Ubuntu:6.06/dapper-security)
Inst python-uno [2.0.2-2ubuntu12] (2.0.2-2ubuntu12.1 Ubuntu:6.06/dapper-security)
Inst openoffice.org-writer [2.0.2-2ubuntu12] (2.0.2-2ubuntu12.1 Ubuntu:6.06/dapper-security)
Inst openoffice.org-calc [2.0.2-2ubuntu12] (2.0.2-2ubuntu12.1 Ubuntu:6.06/dapper-security)
Inst openoffice.org-draw [2.0.2-2ubuntu12] (2.0.2-2ubuntu12.1 Ubuntu:6.06/dapper-security)
Inst openoffice.org-impress [2.0.2-2ubuntu12] (2.0.2-2ubuntu12.1 Ubuntu:6.06/dapper-security)
Inst openoffice.org-math [2.0.2-2ubuntu12] (2.0.2-2ubuntu12.1 Ubuntu:6.06/dapper-security)
Inst openoffice.org-java-common [2.0.2-2ubuntu12] (2.0.2-2ubuntu12.1 Ubuntu:6.06/dapper-security)
Inst openoffice.org-base [2.0.2-2ubuntu12] (2.0.2-2ubuntu12.1 Ubuntu:6.06/dapper-security)
Inst openoffice.org [2.0.2-2ubuntu12] (2.0.2-2ubuntu12.1 Ubuntu:6.06/dapper-security)
Inst openoffice.org-evolution [2.0.2-2ubuntu12] (2.0.2-2ubuntu12.1 Ubuntu:6.06/dapper-security)
Inst openoffice.org-gnome [2.0.2-2ubuntu12] (2.0.2-2ubuntu12.1 Ubuntu:6.06/dapper-security) []
Inst openoffice.org-gtk [2.0.2-2ubuntu12] (2.0.2-2ubuntu12.1 Ubuntu:6.06/dapper-security)
Conf linux-image-2.6.15-26-k7 (2.6.15-26.44 Ubuntu:6.06/dapper-security)
Conf linux-image-k7 (2.6.15.24 Ubuntu:6.06/dapper-security)
Conf linux-restricted-modules-common (2.6.15.11-3 Ubuntu:6.06/dapper-security)
Conf linux-restricted-modules-2.6.15-26-k7 (2.6.15.11-3 Ubuntu:6.06/dapper-security)
Conf linux-restricted-modules-k7 (2.6.15.24 Ubuntu:6.06/dapper-security)
Conf linux-k7 (2.6.15.24 Ubuntu:6.06/dapper-security)
Conf nvidia-glx (1.0.8762+2.6.15.11-3 Ubuntu:6.06/dapper-security)
Conf ttf-opensymbol (2.0.2-2ubuntu12.1 Ubuntu:6.06/dapper-security)
Conf openoffice.org-core (2.0.2-2ubuntu12.1 Ubuntu:6.06/dapper-security)
Conf openoffice.org-common (2.0.2-2ubuntu12.1 Ubuntu:6.06/dapper-security)
Conf openoffice.org-l10n-en-us (2.0.2-2ubuntu12.1 Ubuntu:6.06/dapper-security)
Conf python-uno (2.0.2-2ubuntu12.1 Ubuntu:6.06/dapper-security)
Conf openoffice.org-writer (2.0.2-2ubuntu12.1 Ubuntu:6.06/dapper-security)
Conf openoffice.org-calc (2.0.2-2ubuntu12.1 Ubuntu:6.06/dapper-security)
Conf openoffice.org-draw (2.0.2-2ubuntu12.1 Ubuntu:6.06/dapper-security)
Conf openoffice.org-impress (2.0.2-2ubuntu12.1 Ubuntu:6.06/dapper-security)
Conf openoffice.org-math (2.0.2-2ubuntu12.1 Ubuntu:6.06/dapper-security)
Conf openoffice.org-java-common (2.0.2-2ubuntu12.1 Ubuntu:6.06/dapper-security)
Conf openoffice.org-base (2.0.2-2ubuntu12.1 Ubuntu:6.06/dapper-security)
Conf openoffice.org (2.0.2-2ubuntu12.1 Ubuntu:6.06/dapper-security)
Conf openoffice.org-evolution (2.0.2-2ubuntu12.1 Ubuntu:6.06/dapper-security)
Conf openoffice.org-gtk (2.0.2-2ubuntu12.1 Ubuntu:6.06/dapper-security)
Conf openoffice.org-gnome (2.0.2-2ubuntu12.1 Ubuntu:6.06/dapper-security)


after trying 10 times more it loaded! i have to say that i switched to "description" tab as fast as i could because it logged me out almost intantly then i waited a little and switched to changes tab :) it worked

i tried again and it crashed! i think that it worked was because i switched to description tab - so something must be buggy :)

---

### Post by Seaman on 2006-07-12
Very tricky... I just installed the same packages a few houres ago, without any kind of problems. If I was you I would send a bug report to the synaptic developers. Untill it is fixed, you can write **sudo apt-get upgrade** in your terminal, it does the same thing as when you update all your packages in synaptic.

---

### Post by mlalkaka on 2006-10-17
I have been having the exact same problem. It doesn't happen with all updates. Only some (seemingly arbitrary) updates cause this to happen on my system. I get around it by closing the "Show Details" pane as soon as possible. I hope a buxfix is released soon; I look at the ChangeLog to determine the importance of certain updates.

---

