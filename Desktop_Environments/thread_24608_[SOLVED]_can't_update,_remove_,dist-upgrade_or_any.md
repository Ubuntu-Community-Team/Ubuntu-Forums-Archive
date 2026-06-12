---
title: "[SOLVED] can't update, remove ,dist-upgrade or anything related to apt-get dpkg :("
date: 2005-04-07
forum: Desktop Environments
---

### Post by primeirocrime on 2005-04-07
hey...It must be the fact that I'm almost doing my birthday party...

I get this annoying happening in Synaptic, Apt-get, Update Manager

I get this message in the output 
> 
 apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  liba52-0.7.4 libmpeg3-1
The following packages will be upgraded:
  apt apt-utils dosfstools education-geography education-tasks evolution gem
  gnome-app-install gnome-system-tools gnome-utils mysql-common openoffice.org
  openoffice.org-bin openoffice.org-evolution openoffice.org-gtk-gnome
  openoffice.org-l10n-en openoffice.org-l10n-pt openoffice.org-l10n-pt-br
  openoffice.org-thesaurus-en-us straw system-tools-backends ttf-opensymbol ubuntu-artwork
  ubuntu-docs ubuntu-quickguide update-manager xfce4-mcs-plugins
27 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 375kB/87.0MB of archives.
After unpacking 2593kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main liba52-0.7.4 0.7.4-1 [25.1kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main libmpeg3-1 1.5.4-4 [79.3kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe xfce4-mcs-plugins 4.2.1-1ubuntu2 [270kB]
Fetched 375kB in 11s (33.6kB/s)

Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/available' near line 22722:
 missing package name
E: Sub-process /usr/bin/dpkg returned an error code (2)
root@ubuntu:/home/mongrel #



what can I do to solve this, I searched everywhere but can't find a solution.

---

### Post by p!=f on 2005-04-08
Try...
```

sudo dpkg --clear-avail

```
I had the same symptoms till I discovered it's a bad RAM. Try to run memtest86+ to check yours.
And, of course, happy birthday and all the best! ;)

---

### Post by primeirocrime on 2005-04-08
thanks! it worked like a charm...

as to the ram problem, I don't yet know if I have it. Can I preform the memtest from isnide Gnome? or do I have to reboot to grub and do it from there?

---

