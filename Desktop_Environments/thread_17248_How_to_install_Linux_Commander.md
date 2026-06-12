---
title: "How to install Linux Commander?"
date: 2005-02-27
forum: Desktop Environments
---

### Post by mckswk on 2005-02-27
I've tried to install Linux Commadner but when I type ./configure an error appeared:

loading cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking host system type... configure: error: can not guess host type; you must specify one

How to specify host type?

---

### Post by az on 2005-02-27
What does this app require?  Usually in the requirements, you will see the list of utilities and libraries required (automake, gtk2.0 libraries.)  Get the packages and the -dev packages that you will need (libgtk2.0-dev)

Or just install gnome-commander.

sudo apt-get install gnome-comander

---

### Post by mckswk on 2005-02-27
Thanks a lot, I've installed gnome-commander:)

Linux Commander requires gtk+ 1.2.x  and glib 1.2.x. I will try to install these packages.

---

### Post by Cariboo1938 on 2006-09-18
> **azz said:**
> 
Or just install gnome-commander.

sudo apt-get install gnome-comander I tried to install gnome-commander that way and got a long list of dependency problems and this message:> Downgrade the following packages:
gnome-commander [1.2.0-3build1 (now) -> 1.1.7-0ubuntu1 (dapper)]
Does it mean, that I cannot install the newest Gnome Commander release?

---

### Post by herrdoktor330 on 2006-09-20
> **Cariboo1938 said:**
> I tried to install gnome-commander that way and got a long list of dependency problems and this message:Does it mean, that I cannot install the newest Gnome Commander release?

Yes, I'm having a problem with this as well. Gnome Commander crashes on me all the time and doesn't read Samba Shares. I've gone through all the installed components on my system and Synaptic says I have all the dependancies needed to run the newest GC, but the package installer says otherwise. What did I do wrong?

---

### Post by Cariboo1938 on 2006-09-20
Hi everyone!
:roll:  I'm wondering.....:roll: 
does Gnome Commander function on Dapper 6.06 64 Bit version at all?

---

