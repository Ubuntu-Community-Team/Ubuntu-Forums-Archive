---
title: "newbie here"
date: 2007-08-21
forum: Desktop Effects &amp; Customization
---

### Post by empress on 2007-08-21
I extracted the fluxbox tar and when i did " ./configure C compiler cannot create executables. 

...
checking whether the C compiler (gcc  ) works... no 
configure: error: installation or configuration problem: C compiler 
cannot create executables. 

not only with fluxbox but also with xine player.
do i need to install anything else?

---

### Post by reckless2k2 on 2007-08-21
go to synaptic and install all that goodness. don't sweat compiling if you don't have to. adminsitration menu and synaptic. search..yadda.

---

### Post by RedSquirrel on 2007-08-22
> **empress said:**
> I extracted the fluxbox tar and when i did " ./configure C compiler cannot create executables. 

...
checking whether the C compiler (gcc  ) works... no 
configure: error: installation or configuration problem: C compiler 
cannot create executables. 

not only with fluxbox but also with xine player.
do i need to install anything else?

Note that there is a version of Fluxbox in the repositories:

```
sudo apt-get install fluxbox && sudo update-menus
```To install the tools for compiling:

```
sudo apt-get install build-essential
```If you decide to compile Fluxbox, it's a good idea to run:

```
sudo apt-get build-dep fluxbox
```to install the dependencies you will need for the build.

---

