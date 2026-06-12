---
title: "KDE 3.4 Window Decorations"
date: 2005-03-14
forum: Desktop Environments
---

### Post by SysFail on 2005-03-14
I have been trying to install some new window decorations and even though I get them to compile all the way, they REFUSE to show up in the control panel look and feel section so I can select them....does anybody know where these window decoration files are supposed to be stored at?????? If anybody has had success installing new ones please let me know!!

Thank you...

---

### Post by fdoving on 2005-03-15
It's always best to use .deb packages. 
If you try to compile from sources, you'll atleast need the libqt dev packages, probably kdelibs-dev too.

And you need to do './configure --prefix=/usr' before make.

The placing of files.. I'd recommend using checkinstall (apt-cache show checkinstall) instead of 'make install'. 
That'll give you a easily manageable .deb package.

---

### Post by Cybermagellan on 2005-03-15
[QUOTE=SysFail]I have been trying to install some new window decorations and even though I get them to compile all the way, they REFUSE to show up in the control panel look and feel section so I can select them....does anybody know where these window decoration files are supposed to be stored at?????? If anybody has had success installing new ones please let me know!!

Thank you...[/QUOTE]
 I believe (don' take me as law here) but you have to create the home/.kde/apps/themes folder or something along those lines. Once you do that anything you extract in there will (aka should) show up. HTH

Shawn

---

