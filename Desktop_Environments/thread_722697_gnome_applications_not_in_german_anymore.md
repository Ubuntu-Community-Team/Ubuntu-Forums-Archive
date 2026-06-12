---
title: "gnome applications not in german anymore"
date: 2008-03-12
forum: Desktop Environments
---

### Post by tekknokrat on 2008-03-12
I had my apps running in german in past, but for some reasons it doesn't really works anymore.
Gnome Applications doesnt start in another language. Some menu entries in gnome are shown in german but most of the apps eg. gimp and tomboy only starts in english.

I have tried to start via gdm and kdm with kde- and gnomesession.
Systemlanguage is german and this works fine for kde apps. 
I changed language with qt-language-selector and gnome-language-selector with no difference.

> language-pack-de
language-pack-kde-de
language-pack-gnome-de

+ deps are installed.

my locales looks this:

> LANG=de_DE
LANGUAGE=de_DE:de
LC_CTYPE="de_DE"
LC_NUMERIC="de_DE"
LC_TIME="de_DE"
LC_COLLATE="de_DE"
LC_MONETARY="de_DE"
LC_MESSAGES="de_DE"
LC_PAPER="de_DE"
LC_NAME="de_DE"
LC_ADDRESS="de_DE"
LC_TELEPHONE="de_DE"
LC_MEASUREMENT="de_DE"
LC_IDENTIFICATION="de_DE"
LC_ALL=

I tried a lot but no chance for fixing this, can sombody lend me a hand please? :confused:

---

### Post by tekknokrat on 2008-03-16
reinstall of gutsy solved lacking german support. But the mysterious of the problem will resist. Perhaps theres was something broken from beginning when switching from server to desktop.

---

