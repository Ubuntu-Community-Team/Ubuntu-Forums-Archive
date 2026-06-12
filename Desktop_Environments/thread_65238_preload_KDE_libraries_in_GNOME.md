---
title: "preload KDE libraries in GNOME"
date: 2005-09-13
forum: Desktop Environments
---

### Post by arthur_kalm on 2005-09-13
Hello,

I use a lot of KDE apps in Ubuntu but they always take forever to load. I was wondering if there is a way to load KDE libraries during boot to get them to open faster. Thanks.

---

### Post by felix.rommel on 2006-01-11
I think you can load kdeinit while starting Gnome. Haven't tried this but should work:

Sorry have german version so names might differ...

1. > System > Preferences > Sessions

2. There klick on the right tab "Startup Programs"

3. Then klick on add.

4. Enter the following in the field "Startup Command": 

kdeinit

Klick OK and log out of Gnome and log in again. Then the KDE libraries should be loaded on Gnome start so that all the other KDE applications start quick.

---

