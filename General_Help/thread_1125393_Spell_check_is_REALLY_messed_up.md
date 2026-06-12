---
title: "Spell check is REALLY messed up"
date: 2009-04-14
forum: General Help
---

### Post by Nano_ext3 on 2009-04-14
Hi,

I don't know why, but in any* app that supports spell check, i.e. Tomboy Notes or Open Office 3.0-base, EVERY word is red underlined.  I uninstalled open office and re-installed, no luck

Any help?  How to reinstall the dictionaries?

@.@

THANKS!

---

### Post by askreet on 2009-04-14
Try:
```
sudo dpkg-reconfigure dictionaries-common
```

That will let you re-select your default dictionary.

---

### Post by der_vegi on 2009-05-03
Are you using German localisation? The spell checker is broken due to hunspell-de-med, see launchpad bug 363619 and bug 363619.
Workaround:
```
sudo apt-get remove hunspell-de-med
```

---

### Post by Nano_ext3 on 2009-05-03
Installing aspell-en was the trick, and then I had to get the enlish pack for OO.o 3 off the website:

[http://wiki.services.openoffice.org/wiki/Dictionaries](http://wiki.services.openoffice.org/wiki/Dictionaries)

Apparently, OO.o 3 never installed the enlish dictionary, so I had to browse to the OO.o 3 dir on my PC and install the file for english.  I dont know why it didnt get installed on isntallation.

---

### Post by Nano_ext3 on 2009-05-03
I believe the dictionaries are in "./opt/openoffice/basis-link/program/resource" if im not mistaken


EDIT:

Whooos here:

"./opt/openoffice/share/extension/install"

They are .oxt files

---

