---
title: "KDE secondary Alt+Tab feature missing in Gutsy"
date: 2007-11-05
forum: Desktop Environments
---

### Post by SadaraX on 2007-11-05
I am using KDE with Kubuntu 7.10 Gutsy. Under the previous Kubuntu 7.04 Feisty, my alt-tab keys behaved differently than they do now.

Previously, my left-alt key + tab would cycle through all the running programs, and my right-alt+tab would toggle between the last two focused windows (without cycling other programs).

Currently, both alt+tabs cycle through all programs. I would like to know how I can get my right-alt+tab feature for quick toggle focus. Any help?

---

### Post by bodyglove on 2007-11-13
I really would like to see this feature back... 

so :

/signed

---

### Post by bodyglove on 2007-11-14
remove the following line in
.kde/share/config/kwinrc

AltTabStyle=CDE

then it works only with the last active window, or cycle through all windows

---

