---
title: "xserver-xorg failed error"
date: 2007-11-16
forum: Debian
---

### Post by deepclutch on 2007-11-16
Hi,
I am using debian sid apt-pinned with testing.
after installation.i got below error:
```
 My message when running apt-get -f install:-
dpkg: dependency problems prevent configuration of xorg:
 xorg depends on xserver-xorg; however:
  Package xserver-xorg is not configured yet.
dpkg: error processing xorg (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xserver-xorg
 xorg
```
what is the possible solution.i tried --force options too.but doesnot install.please help.

---

### Post by ZipoTe on 2007-11-16
can you explain a littlle more? did you have this packets installed prevously? they dissapeared?:confused: maybe it's just:
sudo dpkg-reconfigure xserver-xorg

---

### Post by deepclutch on 2007-11-17
yes.it was a bug in the version.i got update for xserver-xorg yesterday and debian is working fine :) btw,thx.

---

