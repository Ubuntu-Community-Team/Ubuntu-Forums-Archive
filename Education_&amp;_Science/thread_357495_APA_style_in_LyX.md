---
title: "APA style in LyX"
date: 2007-02-09
forum: Education &amp; Science
---

### Post by chocolatemintmocha on 2007-02-09
Does anyone know how to use the APA document layout in LyX? The document class section in the Document Settings window shows Unavailable: article (APA). I did find a file named apa.layout in /usr/share/lyx/layouts, but LyX doesn't seem to see it. Any suggestions are welcome. Thanks

---

### Post by parktownprawn on 2007-02-09
The file apa.layout only tells Lyx how to deal with the apa package it isn't the apa package it self.

you probably need to install the apa and apacite packages from ctan.

 [http://tug.ctan.org/cgi-bin/ctanPackageInformation.py?id=apacite](http://tug.ctan.org/cgi-bin/ctanPackageInformation.py?id=apacite)
[http://tug.ctan.org/cgi-bin/ctanPackageInformation.py?id=apa](http://tug.ctan.org/cgi-bin/ctanPackageInformation.py?id=apa)

see [https://help.ubuntu.com/community/LaTeX](https://help.ubuntu.com/community/LaTeX) for help for installing latex packages

alternatively you can install the texlive packages 

texlive-publishers
texlive-bibtex-extra

(this will probably install a whole lot of other stuff you don't need)

Once you've installed the packages open lyx and run  Tools>Reconfigure and restart lyx

---

### Post by chocolatemintmocha on 2007-02-10
Thanks!:)

---

