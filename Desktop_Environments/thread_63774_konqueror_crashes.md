---
title: "konqueror crashes"
date: 2005-09-09
forum: Desktop Environments
---

### Post by meff on 2005-09-09
Just about every 5 mins after I load up a konqueror file browser or web browser it crashes.. Every single time.

I am running 5.04 ubuntu w/ kubuntu-desktop installed.. Everything else seems to be fine.
P4 2.2 1GB RAM

Anyone else have this issue or any ideas on how to fix?

Thanks all.
-r

---

### Post by Gezzer on 2005-09-09
it seems to be a bug with KDE3.4 u can place this in your apt-conf file and upgrade to KDE3.4.2 which seems to fix the problem ...

##KDE342
deb [http://kubuntu.org/hoary-kde342](http://kubuntu.org/hoary-kde342) hoary-updates main
deb-src [http://kubuntu.org/hoary-kde342](http://kubuntu.org/hoary-kde342) hoary-updates main

---

### Post by meff on 2005-09-09
[QUOTE=Gezzer]it seems to be a bug with KDE3.4 u can place this in your apt-conf file and upgrade to KDE3.4.2 which seems to fix the problem ...

##KDE342
deb [http://kubuntu.org/hoary-kde342](http://kubuntu.org/hoary-kde342) hoary-updates main
deb-src [http://kubuntu.org/hoary-kde342](http://kubuntu.org/hoary-kde342) hoary-updates main[/QUOTE]

Thank-you, I am trying now!
-r

---

### Post by meff on 2005-09-09
[QUOTE=meff]Thank-you, I am trying now!
-r[/QUOTE]
 Ok, seems to have fixed konqueror crashing, but I have no idea where the KDE Control Panel link went.. For now I can launch kcontrol from 'Run Application' .. but do you know what happened to it?

Thanks :)

---

