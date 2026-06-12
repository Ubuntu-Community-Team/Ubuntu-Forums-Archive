---
title: "Xubuntu desktop - apt-get vs aptitude issue"
date: 2006-08-12
forum: Desktop Environments
---

### Post by Mandor on 2006-08-12
Today I installed a fresh base system and I wanted to install xubuntu-desktop. I noticed that "sudo apt-get install xubuntu-desktop"  propose  total install of few hundred  megabytes  and  "sudo aptitude install  xubuntu desktop"  propose  over  a gigabyte.  This  is  the  final  storage  for the  installed packages. Why there is such a difference in the dependancies  between apt-get and apitude. I thouth that in that respect it they should be equal.

---

### Post by iamhugeinjapan on 2006-08-13
I run a base xubuntu and just looked at what it would take to install kubuntu-desktop

apt-get:download 304MB, uses 1025MB, installs 361 packages 21 not upgraded

aptitude: download 413MB, uses 1289MB, installs 419 packages, 21 not upgraded


I'm not sure of the differences without carefully studying the list of packages. I assume aptitude is pulling down 'recommended' dependencies along with the required ones.

---

### Post by maniacmusician on 2006-08-13
yes that is most likely the case. aptitude automatically downloads and installs suggested packages while apt-get simply *suggests* them.

edit: also, another thing to consider: if you install using apt-get, you won't be able to easily remove xubuntu-desktop, as it will read it as just a metapackage. if you use aptitude, then if you ever want to uninstall you can do it by simply typing sudo aptitude remove xubuntu-desktop.

---

### Post by 5-HT on 2006-08-13
[quote=maniacmusician]yes that is most likely the case. aptitude automatically downloads and installs suggested packages while apt-get simply *suggests* them. [/quote]

Just to add how you can disable aptitude's default setting of treating recommended packages as dependencies:

1. For a one-time thing:
```
 sudo aptitude -R install <package> 
```

2. A more permanent solution:
There's an option for it in aptitude's pseudo-gui (you could also edit some of aptitude's config files, but this method does that for you. If you wanted to manually edit the configs the user guide found in  /usr/share/aptitude/README describes all options).

---

### Post by dolby on 2006-08-13
imo its generally better to use aptitude when installing such huge amount of packages in order to be able to safely remove if sth goes wrong or any reason at all afterwards..

---

### Post by ardchoille on 2006-08-13
> **maniacmusician said:**
> yes that is most likely the case. aptitude automatically downloads and installs suggested packages while apt-get simply *suggests* them.

edit: also, another thing to consider: if you install using apt-get, you won't be able to easily remove xubuntu-desktop, as it will read it as just a metapackage. if you use aptitude, then if you ever want to uninstall you can do it by simply typing sudo aptitude remove xubuntu-desktop.

Yes, aptitude tracks deps while the current version of apt-get does not. I submitted a bug about this apt-get behaviour and the devs are adding support for this in the apt-get that will ship with Edgy Eft - apt-get will have a new option (I believe it is --auto-remove) which will remove the deps as well as the app itself. Only bug I ever filed.. glad to see the Ubuntu devs really listen :)

---

