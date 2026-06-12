---
title: "Printer advanced menu no longer available in 18.04"
date: 2018-08-10
forum: Desktop Environments
---

### Post by vansven on 2018-08-10
In Kubuntu 16.04, when printing from e.g. Okular, I have for the printer  under "Properties" the menues "Page" and "Advanced" where in the "Advanced"  menu I'm able to set options for the printer driver, e.g. color  printing and stapling.

After upgrading to Kubuntu 18.04 printing still works. However, I have no longer the "Advanced" menu for the same printer so I can no longer select e.g. color  printing and stapling. Under "Properties"  I have the menues "Page" and "Job Options", i.e., no "Advanced" menu. In the new "Job Options" menu I'm not able  to set options for the printer driver like color  printing and stapling. Where can I find the content of  the "Advanced" menu that I had available in 16.04?

Thanks / Van

---

### Post by Autodave on 2018-08-10
Did you upgrade from 16.04 or do a clean install?  What is make and model of printer and how is it connected to PC?

---

### Post by vansven on 2018-08-11
I've tried both on different computers, i.e. upgrading from 16.04 to 18.04 and a clean install of 18.04, but in both cases I cannot find  the "Advanced"  menu for the printer  under "Properties". I've tested different printers and to me it seems like the "Advanced" menu is always available for all printers in 16.04, e.g. for the printer "HP LaserJet p4015", but the "Advanced" menu is not available for any printer in 18.04.

Can you please confirm that you have the "Advanced"  menu for your printer  under "Properties" in 18.04 when printing from Okular?

---

### Post by Autodave on 2018-08-11
I do not have Okular*, sorry.*

---

### Post by vansven on 2018-08-12
The problem seems to be that Okular uses Qt for printing and the Qt-version used in Kubuntu 18.04 is not able to show the advanced CUPS options. That's sad because it was possible in the Qt-version used in Kubuntu 16.04. In recent versions of Qt it seems to have been fixed, see [https://www.kdab.com/better-support-for-cups-features-in-qt-5-11/](https://www.kdab.com/better-support-for-cups-features-in-qt-5-11/). I really would like to get a patch for my Kubuntu 18.04 installation to enable the advanced menu.

---

