---
title: "Gnome Panels not avaliable"
date: 2009-08-30
forum: Desktop Environments
---

### Post by bigmac1990 on 2009-08-30
I think i've unistalled my gnome panels. I have tried running "gnome-panel" to get them back but it keeps saying something about gnome not being available. Is there any way i can get gnome back so i can use my pc again?

Thanks for any help

---

### Post by earthpigg on 2009-08-30
odd.

try this: 

sudo apt-get install ubuntu-desktop

if that doesn't do it, try logging in as a different user - create one if you must. do the panels work there?

the answer will tell us how to restore the panels when using your username.

---

### Post by bigmac1990 on 2009-08-30
I've tried that line and it doesn't recognize anythings missing so won't download any packages.
Also it won't let me log in as another user because it goes straight to desktop and won't let me get back (using Ctrl, Alt Backspace) to the menu to choose another user.

---

### Post by earthpigg on 2009-08-30
try this:

> sudo killall Xorg

notice it is an X, not an x.

---

