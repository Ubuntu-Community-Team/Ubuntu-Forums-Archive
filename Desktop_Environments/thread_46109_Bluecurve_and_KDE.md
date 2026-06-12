---
title: "Bluecurve and KDE"
date: 2005-07-03
forum: Desktop Environments
---

### Post by nbx909 on 2005-07-03
I installed the bluecurve theme useing the 1st way as described [here](http://ubuntuforums.org/archive/index.php/t-2696.html) It works in gnome great but i can not get it to work correctly in kde. Is there a way to get the bluecurve theme to work in KDE?

---

### Post by Lord Illidan on 2005-07-03
I don't think bluecurve is a KDE theme...it is a Gnome theme, so it will not work on KDE...AFAIK

---

### Post by nbx909 on 2005-07-03
No when i had FC4 i had bluecurve as my KDE theme...

---

### Post by Lord Illidan on 2005-07-03
But Fedora Core is for gnomeaholics...IMHO...
Well...I will check..

---

### Post by nbx909 on 2005-07-03
i don't really like gnome... i don't know why... i like xfce and kde.. blackbox is cool too....

---

### Post by Morimando on 2005-07-03
[QUOTE=nbx909]i don't really like gnome... i don't know why... i like xfce and kde.. blackbox is cool too....[/QUOTE]
maybe it's because it looks somewhat antique? Just a thought ;) Well, go to the KDE homepage and look through the themes they got there, maybe they got something similar. Also you can pay [www.freshmeat.net](www.freshmeat.net) a visit

---

### Post by Lord Illidan on 2005-07-03
I happen to love KDE, and also, I am developing a liking for Afterstep...Though Gnome looks somewhat Windoze 95 ish...ugh horrible...

---

### Post by smoon on 2005-07-03
[QUOTE=nbx909]I installed the bluecurve theme useing the 1st way as described [here](http://ubuntuforums.org/archive/index.php/t-2696.html) It works in gnome great but i can not get it to work correctly in kde. Is there a way to get the bluecurve theme to work in KDE?[/QUOTE]

Try the [QtCurve Theme](http://www.kde-look.org/content/show.php?content=5065). Or the original [Redhat Artwork](http://fedora.redhat.com/projects/artwork/) [RPM](http://download.fedora.redhat.com/pub/fedora/linux/core/development/i386/Fedora/RPMS/redhat-artwork-0.124-2.i386.rpm). You can transform the RPM into a Debian package with alien. Even though the KDE style is included it does not work since Fedora seems to use another path for KDE styles than Ubuntu. You'll have to fix that manually - but it should work somehow.

Another way is to grab the Fedora artwork via CVS and create a package yourself with checkinstall - I did it once and it worked just fine.

But I suggest you use the QtCurve tarball and create a Debian package out of it with checkinstall. This will be the most painless way IMHO.

---

