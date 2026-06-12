---
title: "[SOLVED] KDE4 notes not working in Hardy"
date: 2008-11-03
forum: Desktop Environments
---

### Post by arch0njw on 2008-11-03
I hope the only answer is not "upgrade to 8.10"...

The notes applet has never worked for me in Hardy.  I am just finally getting around to posting about it (perhaps I am lazy).

If someone could even only point me to a configuration file where the entry is *supposed* to appear, that would be a help.  I cannot find anything at this point.

TIA.

---

### Post by arch0njw on 2008-11-04
Per this link ([http://forum.kde.org/showthread.php?tid=11344&pid=14142#pid14142](http://forum.kde.org/showthread.php?tid=11344&pid=14142#pid14142)), the problem was having the wrong package installed.  "Everywhere" says to install the *extragear-plasma* package, but apparently the right package to install is *kdeplasma-addons*.  When I installed the latter, it notified me the former (and the data package) would be removed.

That simple.

---

