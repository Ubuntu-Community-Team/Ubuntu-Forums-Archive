---
title: "KDE4 Installing Opera 9.50b2"
date: 2008-04-28
forum: Desktop Environments
---

### Post by lodravah on 2008-04-28
'lu all

I just had my first peek at KDE4 yesterday, and it looks really good, even though it is a work in progress. I like to use the newest stuff all the time, and KDE4 is a challenge. But I had one issue when trying to install Opera 9.50b2 from a downloaded .deb - package. Usually when I install Opera, I just click the package and is then able to install it, but when I tried this with KDE4, I just got an empty package, and such nothing to install. Does the direct installing of .deb's not work in KDE4?

Any ideas?

---

### Post by luisromangz on 2008-04-28
That's a distro integration feature, as there are many distros which will use KDE4 (hopefully) and not all of them are deb based. So it's more a Kubuntu integration issue more than a KDE4.

---

### Post by Metallion on 2008-04-28
Try opening a terminal and type:

dpkg -i path_to_your_opera_package.deb

---

### Post by der_joachim on 2008-04-28
Check whether the package gdebi-kde is installed. Opera and gdebi seem to like each other. :)

---

