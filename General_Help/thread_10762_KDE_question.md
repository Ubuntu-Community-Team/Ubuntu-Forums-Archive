---
title: "KDE question"
date: 2005-01-11
forum: General Help
---

### Post by konan on 2005-01-11
Is it possible to install KDE on Ubuntu? If it's possible, how could I do that?

P.s.:I'm quit a nOOb...

---

### Post by nocturn on 2005-01-11
[QUOTE=konan]Is it possible to install KDE on Ubuntu? If it's possible, how could I do that?

P.s.:I'm quit a nOOb...[/QUOTE]

Activate the universe repository (There is a repositories entry in one of the synaptic menus or you can edit /etc/apt/sources.lst - removing the # before universe).

Then either use synaptic:
reload button
search: kde
select for install
apply

Or a terminal
sudo aptitude update
sudo install kde

At the next login, select a KDE session in the Gnome Display Manager.

---

### Post by konan on 2005-01-11
Thank you VERY MUCH!!!

---

