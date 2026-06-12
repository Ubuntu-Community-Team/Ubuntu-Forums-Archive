---
title: "Installing Themes on Kubuntu"
date: 2005-12-10
forum: Desktop Environments
---

### Post by Rochvellon on 2005-12-10
Ok, I apologize for asking too many questions, but I can't really help it. How do I install themes on KDE? Because I don't see any "add theme" button... I already have downloaded it, it's in a folder on my desktop... what next?

---

### Post by OneWingedAngel on 2005-12-10
Do you mean a colour scheme, a widget style or a window manager theme?. If it's a colour scheme, you can import it using

Appearance - Colours - Import Scheme...

If it's one of the other two, it depends on whether it's a .deb file or a source package (.tar.bz2 or .tar.gz). If it's a .deb, just install it using

$ sudo dpkg -i <filename.deb>

If it's a source package, you have to build it. Make sure you have the KDE dev packages installed (sudo apt-get install kde-devel), then do the following:

(for .tar.gz):
$ tar zxvf <filename.tar.gz>
(for .tar.bz2):
$ tar jxvf <filename.tar.bz2>
$ cd <dirname> (where the package extracted to)
$ ./configure --prefix=`kde-config --prefix` (backticks, not apostrophes)
$ make
$ sudo make install

Hope this helps.

---

### Post by limit223 on 2005-12-10
[QUOTE=Rochvellon]...How do I install themes on KDE? Because I don't see any "add theme" button... I already have downloaded it, it's in a folder on my desktop... what next?[/QUOTE]


Click Kmenu - Run command - type: kcontrol -  Appearance & Themes - Theme Manager - **Install New Theme** button

---

### Post by Rochvellon on 2005-12-10
[quote=limit223]Click Kmenu - Run command - type: kcontrol -  Appearance & Themes - Theme Manager - **Install New Theme** button[/quote] Thanks!=D>

---

