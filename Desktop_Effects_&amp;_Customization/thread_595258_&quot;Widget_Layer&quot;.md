---
title: "&quot;Widget Layer&quot;?"
date: 2007-10-28
forum: Desktop Effects &amp; Customization
---

### Post by ErusGuleilmus on 2007-10-28
I heard from somewhere that Compiz Fusion has a widget layer, kind of like the one you find in OS X. With Full desktop Effects on in 8.10. does compiz support this feature? And if so, how and where to I get and add widgets. Thank You.

---

### Post by CarpKing on 2007-10-28
You'll have to install the Compiz-Config Settings Manager to enable the widget layer, I believe.  Once you do, add: 
[CODEdeb http://hendrik.kaju.pri.ee/ubuntu gutsy screenlets
deb-src http://hendrik.kaju.pri.ee/ubuntu gutsy screenlets][/CODE]
to your sources.list and then install "screenlets" from Synaptic or the terminal.  You can find screenlets and information here:  [http://www.screenlets.org/index.php/Category:UserScreenlets](http://www.screenlets.org/index.php/Category:UserScreenlets)

I don't remember how to actually get the screenlets to appear on the widget layer, but I know it can be done fairly easily because I did it before.

EDIT: It can be done either in CCSM under "Widget Layer" by putting "name=Screenlet" under "Behavior" or by right clicking each screenlet and selecting "window--> widget."

---

