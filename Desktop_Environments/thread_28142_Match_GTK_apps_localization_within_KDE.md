---
title: "Match GTK apps localization within KDE"
date: 2005-04-19
forum: Desktop Environments
---

### Post by zeddemore on 2005-04-19
Hello, I'm using KDM/KDE in Kubuntu and I have a problem. I'd like to choose a idiom just to a user session instead to setup a wide system locale configuration, like "sudo dpkg-reconfigure locales". I configured the idiom in KDE Control Center but only KDE applications follow this idiom configurated. I've tried to setup environment variables as follow:

LANG=pt_BR.UTF-8
LC_CTYPE="pt_BR.UTF-8"
LC_NUMERIC="pt_BR.UTF-8"
LC_TIME="pt_BR.UTF-8"
LC_COLLATE="pt_BR.UTF-8"
LC_MONETARY="pt_BR.UTF-8"
LC_MESSAGES="pt_BR.UTF-8"
LC_PAPER="pt_BR.UTF-8"
LC_NAME="pt_BR.UTF-8"
LC_ADDRESS="pt_BR.UTF-8"
LC_TELEPHONE="pt_BR.UTF-8"
LC_MEASUREMENT="pt_BR.UTF-8"
LC_IDENTIFICATION="pt_BR.UTF-8"
LC_ALL=

I saved these configurations in  some files as: ~/.xsession, ~/.profile, ~/.i18n, ~/.bash_profile, but when I  run gedit, this shows texts in en_US, the system wide localization. Any sugestions?

P.S.: I wouldn't like  to change to GDM.  ;-)

---

