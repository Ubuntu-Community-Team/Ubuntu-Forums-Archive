---
title: "OpenOffice and apt-get problems"
date: 2009-01-18
forum: General Help
---

### Post by picpak on 2009-01-18
Both these programs have failed me on Ubuntu 8.10. Here's the breakdown:

1) Whenever I try to open OpenOffice, it will load correctly, and then try to recover an Untitled file. Failing that, it then tells me that OpenOffice has crashed. Here's the output from the terminal:

```
kim@ubuntu:~$ soffice
terminate called after throwing an instance of 'com::sun::star::deployment::DeploymentException'
```

2) apt-get stalls when installing programs. It will get as far as downloading the packages, and then freeze. Here's an example with openoffice.org-gtk (a program I removed in an attempt to fix OpenOffice):

```
kim@ubuntu:~$ sudo apt-get install openoffice.org-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  openoffice.org-gtk
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 153kB of archives.
After this operation, 598kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  openoffice.org-gtk
Install these packages without verification [y/N]? Y
Get:1 http://ppa.launchpad.net intrepid/main openoffice.org-gtk 1:3.0.1~rc1-2ubuntu2~intrepid1 [153kB]
Fetched 153kB in 1s (92.9kB/s)
```

Interestingly enough, if I install and remove programs using dpkg, it works perfectly:

```
kim@ubuntu:~$ sudo dpkg -i /var/cache/apt/archives/openoffice.org-gtk_1%3a3.0.1~rc1-2ubuntu2~intrepid1_i386.deb 
Selecting previously deselected package openoffice.org-gtk.
(Reading database ... 104721 files and directories currently installed.)
Unpacking openoffice.org-gtk (from .../openoffice.org-gtk_1%3a3.0.1~rc1-2ubuntu2~intrepid1_i386.deb) ...
Setting up openoffice.org-gtk (1:3.0.1~rc1-2ubuntu2~intrepid1) ...

kim@ubuntu:~$ sudo dpkg -r openoffice.org-gtk
(Reading database ... 104730 files and directories currently installed.)
Removing openoffice.org-gtk ...
kim@ubuntu:~$ 
```

Any suggestions?

---

### Post by picpak on 2009-01-18
BTW: aptitude does the exact same thing.

---

### Post by pizzicottina88 on 2009-11-09
i also report this error :

 terminate called after throwing an instance of 'com::sun::star::deployment::DeploymentException'

i've tried to erase  the directory "openoffice.org" from my home ,  then i've written " oowriter" ( without ") in the shell and so i' ve resolved this problem.

excuse me for my orrible english.

---

