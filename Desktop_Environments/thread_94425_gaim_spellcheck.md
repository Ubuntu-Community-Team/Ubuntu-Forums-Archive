---
title: "gaim spellcheck"
date: 2005-11-24
forum: Desktop Environments
---

### Post by Jad on 2005-11-24
Hi, 
Spell spellcheck doesn't seems to be working with gaim, I don't even have preferences -> compose.. 
also it's not working in abi word, and OO2, please advise.

```
 dpkg -l | grep aspell ii  aspell                                0.60.3-5                             G NU Aspell spell-checker
ii  aspell-en                             6.0-0-5                              E nglish dictionary for GNU Aspell
ii  libaspell15                           0.60.3-5                             G NU Aspell spell-checker runtime library
ii  libaspell15c2                         0.60.3-5                             G NU Aspell spell-checker runtime library [du
```
```

dpkg -l | grep gaim
ii  gaim                                  1.5.0-1ubuntu3                       multi-protocol instant messaging client
ii  gaim-data                             1.5.0-1ubuntu3                       multi-protocol instant messaging client - da
ii  gaim-themes                           0.1-1                                Smiley themes collection for gaim
```

```
 dpkg -l | grep openoffice
ii  openoffice.org-debian-files           1.1.5-0+1ubuntu1                     Debian specific parts of OpenOffice.org
ii  openoffice.org2                       1.9.129-0.1ubuntu4                   OpenOffice.org Office suite version 2.0
ii  openoffice.org2-base                  1.9.129-0.1ubuntu3                   OpenOffice.org office suite - database
ii  openoffice.org2-calc                  1.9.129-0.1ubuntu4                   OpenOffice.org office suite - spreadsheet
ii  openoffice.org2-common                1.9.129-0.1ubuntu4                   OpenOffice.org office suite architecture ind
ii  openoffice.org2-core                  1.9.129-0.1ubuntu4                   OpenOffice.org office suite architecture dep
ii  openoffice.org2-draw                  1.9.129-0.1ubuntu4                   OpenOffice.org office suite - drawing
ii  openoffice.org2-evolution             1.9.129-0.1ubuntu4                   Evolution Addressbook support for OpenOffice
ii  openoffice.org2-gnome                 1.9.129-0.1ubuntu4                   GNOME Integration for OpenOffice.org (Widget
ii  openoffice.org2-impress               1.9.129-0.1ubuntu4                   OpenOffice.org office suite - presentation
ii  openoffice.org2-java-common           1.9.129-0.1ubuntu4                   OpenOffice.org office suite Java support arc
ii  openoffice.org2-kde                   1.9.129-0.1ubuntu4                   KDE Integration for OpenOffice.org (Widgets,
ii  openoffice.org2-l10n-en-us            1.9.129-0.1ubuntu4                   English_american language package for OpenOf
ii  openoffice.org2-math                  1.9.129-0.1ubuntu4                   OpenOffice.org office suite - equation edito
ii  openoffice.org2-writer                1.9.129-0.1ubuntu4                   OpenOffice.org office suite - word processor
```

```
dpkg -l | grep abiword
ii  abiword-common                        2.4.1-1ubuntu1                       WYSIWYG word processor based on GTK2
ii  abiword-gnome                         2.4.1-1ubuntu1                       WYSIWYG word processor based on GTK2/GNOME2
ii  abiword-plugins-gnome                 2.4.1-1ubuntu1                       plugins for AbiWord (with GNOME dependency)
```

---

### Post by dcstar on 2005-11-24
[QUOTE=Jad]Hi, 
Spell spellcheck doesn't seems to be working with gaim, I don't even have preferences -> compose.. 
also it's not working in abi word, and OO2, please advise.
.......[/QUOTE]
In OO2, go to File-Wizards-Install New Dictionaries and see if it runs for you.

---

### Post by adbot asdakjsfhs on 2008-03-24
I don't know of a way to enable/disable spell checking in gaim. It always worked for me when I have all packages required. 

You must install some aspell dictionary as well, otherwise spell checking will not work.

---

