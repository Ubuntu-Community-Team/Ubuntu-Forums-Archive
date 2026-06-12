---
title: "Kubuntu Netbook Remix (lucid) no window borders"
date: 2010-05-03
forum: Desktop Environments
---

### Post by metalshark on 2010-05-03
After upgrading from Karmic to Lucid on Kubuntu Netbook Remix, the window borders and titlebars have all disappeared. Using the Alt-Click trick allows me to see them on a per-window basis, but I wish to restore the old behaviour.

Maximus is not installed or running and there appears to be a bug when using Microsoft Office 2007 in CrossOver Office as the drop down menu of KDE blanks out the top half of the ribbon interface.

Does anyone know how to turn off this maximising windows nonsense on Kubuntu?

---

### Post by metalshark on 2010-05-03
OK at least have the proper maximise behaviour now.

Do an Alt-F3, click on Configure Window Behaviour and under Advanced change the positioning to Smart.

The drop-down menu's issue with Wine programs still persists though (it's like it is owning the Xorg expose region, even when it is not visible).

---

### Post by antoniok on 2010-05-14
Hi there! I manage to fix this problem by doing the following:

Edit the file

/usr/share/kubuntu-netbook-default-settings/share/config/kwinrc

in the [Windows] section change the

BorderlessMaximizedWindows=true

to

BorderlessMaximizedWindows=false

and the logout and login.

I hope it will work for you too!

---

