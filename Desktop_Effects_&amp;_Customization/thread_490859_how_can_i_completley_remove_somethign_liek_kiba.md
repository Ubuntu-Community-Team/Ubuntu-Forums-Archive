---
title: "how can i completley remove somethign liek kiba"
date: 2007-07-02
forum: Desktop Effects &amp; Customization
---

### Post by searayman on 2007-07-02
i got a script to install kiba with but it wont work even after i uninstalled kiba because it says certain thigns are still installed, so what command can i use to completley remove something?

---

### Post by number3pencil on 2007-07-03
if you want to remove kiaba dock completely, try running

sudo apt-get remove --purge kiba-dock kiba-dock-dev kiba-plugins

---

### Post by SantinoC on 2008-03-06
> **number3pencil said:**
> if you want to remove kiaba dock completely, try running

sudo apt-get remove --purge kiba-dock kiba-dock-dev kiba-plugins

i tried that and this is the output:

> santino@pixxl-ubuntu:~$ sudo apt-get remove --purge kiba-dock kiba-dock-dev kiba-plugins
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kiba-dock

---

### Post by russo.mic on 2008-03-06
Did you compile kiba from source the first install your trying to get rid of?  if so, you just need to run the uninstall script in the source directory,  something like

sudo make uninstall

if my memory serves me

Good Luck!

---

### Post by SantinoC on 2008-03-07
> **russo.mic said:**
> Did you compile kiba from source the first install your trying to get rid of?  if so, you just need to run the uninstall script in the source directory,  something like

sudo make uninstall

if my memory serves me

Good Luck!

thanks, unfortunately that did not work.

yes i did compile it from source.

this is the output:

> santino@pixxl-ubuntu:~/kiba-dock$ sudo make uninstall
make: *** No rule to make target `uninstall'.  Stop.

---

### Post by chunchengch on 2008-03-07
try these commands to find out all kiba files and then delete manually.

$ sudo slocate -u
$ slocate kiba*

---

### Post by SantinoC on 2008-03-07
> **chunchengch said:**
> try these commands to find out all kiba files and then delete manually.

$ sudo slocate -u
$ slocate kiba*

awesome thanks, that seemed to have worked

---

