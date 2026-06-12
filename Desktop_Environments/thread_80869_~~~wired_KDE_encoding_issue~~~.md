---
title: "~~~wired KDE encoding issue~~~"
date: 2005-10-23
forum: Desktop Environments
---

### Post by piggyaugu on 2005-10-23
Constantely I work with some chinese and non-ASCII symbols. They are all OK under GNOME. 

I've configured all locales to UTF8. The webpages and stuffs in menu under KDE are OK. But the open/save dialog and Kconsole is acting strange. They just refuse to display the UTF symbols. 

How can I configure the locale settings under KDE?????

:confused: :confused: 

Any suggestion is appreciated

---

### Post by bertilow on 2005-10-23
[QUOTE=piggyaugu]Constantely I work with some chinese and non-ASCII symbols. They are all OK under GNOME. 

I've configured all locales to UTF8. The webpages and stuffs in menu under KDE are OK. But the open/save dialog and Kconsole is acting strange. They just refuse to display the UTF symbols. [/QUOTE]

"Konsole" seems to have some character encoding/locale bugs in the latest version (3.4.3). I have stopped using it for now, going with Gnome Terminal ("gnome-terminal") instead (no problem using it in KDE). At first I thought something was wrong with my locale installation, but it turned out to be Konsole only. 

I've had no prolems with the open/save dialogs though, probably because I use an English language interface in KDE.

---

