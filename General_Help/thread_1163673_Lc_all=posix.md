---
title: "Lc_all=posix"
date: 2009-05-18
forum: General Help
---

### Post by NekoEx on 2009-05-18
Hello. I've just installed kubuntu-jaunty-kde3 and locale is now set to POSIX (have selected Russia everywhere in the installer, so expected ru_RU.UTF-8 ).
After googling a little tried dpkg-reconfigure locales, and it just rebuilded all the locale files. Then tried to do 'sudo /usr/sbin/update-locale LANG=ru_RU.UTF-8', or to add 'LC_ALL=ru_RU.UTF-8' to /etc/defaults. Both ways didn't help.
Also cleaned up my homedir (moved all dotfiles to backup), it didn't help, too.

What is the 'right' ubuntu-way to configure locales after installation?


oh, also, sorry for ugly thread-name :( and i can't change it now..

---

### Post by NekoEx on 2009-05-19
some kind of bump..

---

### Post by IceBerk on 2009-05-21
Hi, the problem is that KDM3 doesn't export LANG variable. Please, fill new bug at [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug) .
As temporary solution, install GDM instead of KDM

---

