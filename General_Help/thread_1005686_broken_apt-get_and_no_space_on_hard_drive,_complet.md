---
title: "broken apt-get and no space on hard drive, completely stuck"
date: 2008-12-08
forum: General Help
---

### Post by cr4z3d on 2008-12-08
Hey, I've got Ubuntu Eee installed on my Eee 901. Ubuntu is installed on the 4GB partition and I've put /var/log /tmp and /var/tmp on tmpfs to free up space. I then ran an update which had about 40 packages to install. It filled up my remaining space (about 1 gb) and broke my updates with the following error:

```

cr4z3d@leeet:~$ sudo apt-get upgrade
sudo: unable to resolve host leeet
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  openoffice.org-calc: Depends: openoffice.org-core (= 1:2.4.1-1ubuntu2.1) but 1:2.4.1-1ubuntu2 is installed
  openoffice.org-draw: Depends: openoffice.org-core (= 1:2.4.1-1ubuntu2.1) but 1:2.4.1-1ubuntu2 is installed
  openoffice.org-gnome: Depends: openoffice.org-core (= 1:2.4.1-1ubuntu2.1) but 1:2.4.1-1ubuntu2 is installed
  openoffice.org-gtk: Depends: openoffice.org-core (= 1:2.4.1-1ubuntu2.1) but 1:2.4.1-1ubuntu2 is installed
  openoffice.org-impress: Depends: openoffice.org-core (= 1:2.4.1-1ubuntu2.1) but 1:2.4.1-1ubuntu2 is installed
  openoffice.org-writer: Dst Depends: openoffice.org-core (= 1:2.4.1-1ubuntu2.1) but 1:2.4.1-1ubuntu2 is installed
  python-uno: Depends: openoffice.org-core (= 1:2.4.1-1ubuntu2.1) but 1:2.4.1-1ubuntu2 is installed
E: Unmet dependencies. Try using -f.

```

So first instinct was to try sudo apt-get install -f which gave me this error:

```

cr4z3d@leeet:~$ sudo apt-get install -f
sudo: unable to resolve host leeet
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  openoffice.org-core
The following packages will be upgraded:
  openoffice.org-core
1 upgraded, 0 newly installed, 0 to remove and 15 not upgraded.
7 not fully installed or removed.
Need to get 0B/26.8MB of archives.
After this operation, 4096B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 86955 files and directories currently installed.)
Preparing to replace openoffice.org-core 1:2.4.1-1ubuntu2 (using .../openoffice.org-core_1%3a2.4.1-1ubuntu2.1_i386.deb) ...
Unpacking replacement openoffice.org-core ...
dpkg: error processing /var/cache/apt/archives/openoffice.org-core_1%3a2.4.1-1ubuntu2.1_i386.deb (--unpack):
 failed in buffer_write(fd) (10, ret=-1): backend dpkg-deb during `./usr/lib/openoffice/program/vclcanvas.uno.so': No space left on device
Errors were encountered while processing:
 /var/cache/apt/archives/openoffice.org-core_1%3a2.4.1-1ubuntu2.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

At this point I don't know what to do. Where are all these packages being stored so I could delete them and also how do I update everything and not have errors about limited space? Could I move the download location to /home which his on the 16GB partition?

---

### Post by iponeverything on 2008-12-08
you could cache your packages under home:


```
sudo mv /var/cache/apt/archives /home/
sudo ln -s /home/archives /var/cache/apt/
```

---

### Post by cr4z3d on 2008-12-08
Thank you for the quick reply! I was considering a symlink but didn't know if I would run into some sort of problem. This worked and updates are working again. Unfortunately very little space left to really install anything else..

---

