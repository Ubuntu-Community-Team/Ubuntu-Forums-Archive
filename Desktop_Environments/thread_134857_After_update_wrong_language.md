---
title: "After update wrong language"
date: 2006-02-22
forum: Desktop Environments
---

### Post by imiksu on 2006-02-22
I update my responsies and then i wrote command: apt-get upgrade, after many hours after i notice than language has changes from finland to english on gnome-window file-browsing and many other things...

How do i update again from english to finnish?

---

### Post by kaamos on 2006-02-22
I've had this a couple of times with some updates. Just log out of gnome and back in. That should fix it.

---

### Post by imiksu on 2006-02-22
Nope, does not work. Actually now the whole system after gnome-restart is in english :???:

---

### Post by kaamos on 2006-02-22
Whoa. When you open a terminal (Applications->Accessories->Terminal) and type
```
set | grep LANG
```
it should spit out something like this:
> GDM_LANG=fi_FI.UTF-8
LANG=fi_FI.UTF-8
LANGUAGE=fi_FI.UTF-8

If this is not the case, do
```
sudo dpkg-reconfigure locales
```
and set fi_FI.UTF-8 as the default. Then log out&in again.

Hope it works.

---

### Post by imiksu on 2006-02-23
It spits this lines:

LANG=fi_FI.UTF-8
LANGUAGE=fi_FI:fi:en_GB:en

I tried the other command and i think i got english and finnish selected, should it be?

EDIT: I tried to edit the locale.gen and left only the finnish but didn't work out... :S

---

