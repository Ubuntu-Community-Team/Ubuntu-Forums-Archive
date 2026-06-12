---
title: "no shutdown button"
date: 2007-07-13
forum: Dell  Ubuntu Support
---

### Post by NULL712 on 2007-07-13
For some reason my shutdown and restart buttons are gone and most of my options at the login screen. when i click the power button all i get is logout, lock screen, switch user, suspend, and hibernate. and at the login screen all i get is the option to change session and language.

any ideas? i can live with this for now but would like to get this fixed w/o reinstalling ubuntu.

thanx.

---

### Post by kc2keo on 2007-07-17
Did you uninstall the GDM (Graphical Desktop manager)? If you did when you boot your machine up you will boot into the CUI (Character User Interface) login.

If what I said above is not the case then I do not know why your shutdown button and other options are not there. However you can still shut your machine down by doing the following:

from your terminal window (Applications->Accessories->Terminal) type "sudo halt". This will prompt you for your password. Enter it and it will shut your machine down. The halt command shuts your machine down.

---

