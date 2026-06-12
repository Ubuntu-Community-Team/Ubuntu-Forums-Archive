---
title: "help installing dock"
date: 2007-10-28
forum: Desktop Effects &amp; Customization
---

### Post by 40esp on 2007-10-28
Hi,

Im trying to install kiba-dock from svn, and i have filled all requirements as far as dependancies, yet i am getting this error while making/building it




Running 'autoreconf -v --install'...
autoreconf: Entering directory `.'
autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal  --output=aclocal.m4t
aclocal: configure.in: 28: macro `AM_GLIB_GNU_GETTEXT' not found in library
autoreconf: aclocal failed with exit status: 1


any help would be appreciated =]

---

### Post by carlos1992 on 2007-10-28
Use the sinaptics, Kiba is right there

---

### Post by santiagoward2000 on 2007-10-28
> **carlos1992 said:**
> Use the sinaptics, Kiba is right there

Really? Did you add any repositories? It's not in mine.

---

### Post by carlos1992 on 2007-10-30
no i didn't you need repositories for the avant dock but the kiba is easy

---

### Post by carlos1992 on 2007-10-30
but for the kiba you need compiz or beryl
and i wanna dock that use few resources for my old computer

---

### Post by carlos1992 on 2007-10-31
Hey but you need to make available the repositories (universal) the option is in sinaptics but isn't default you have to enable it (setting-->repositories-->third parties (also source code)) :popcorn:

---

### Post by greg142 on 2007-10-31
after installing dock i get this msg in the terminal when i try to start kiba


Failed to locate Plugins at '/usr/local/lib/kiba-dock'
Please install the Plugins at '/usr/local/lib/kiba-dock' or use the '--plugin-pa

anyone help me out?

---

### Post by carlos1992 on 2007-11-09
hey you need to find in your /home/xxx/ the folder named .kiba or similar and move it (sudo mv /home/xxx/.kiba usr/local/lib/kiba-dock) just that:lolflag:

---

