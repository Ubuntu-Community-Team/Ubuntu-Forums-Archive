---
title: "Gnome Shell failing to intialize install in 11.04"
date: 2011-03-26
forum: Desktop Environments
---

### Post by Sketches on 2011-03-26
I have tried to follow the instructions as posted here

[http://live.gnome.org/GnomeShell/DistributionPackages](http://live.gnome.org/GnomeShell/DistributionPackages)

I have fully updated my system and tried this several times

here are the terminal results

sudo add-apt-repository ppa:ricotz/testing

conor@conor-Studio-1537:~$ sudo add-apt-repository ppa:ricotz/testing
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 38AE4F60E356CE050312FA1775CFD31C9E5DB0C8
gpg: requesting key 9E5DB0C8 from hkp server keyserver.ubuntu.com
gpg: key 9E5DB0C8: "Launchpad PPA for Rico" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

sudo apt get update for the ricotz ppa

W: Failed to fetch [http://ppa.launchpad.net/ricotz/testin/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/ricotz/testin/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/ricotz/testin/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/ricotz/testin/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found

 sudo apt-get install gnome-shell
conor@conor-Studio-1537:~$  sudo apt-get install gnome-shell
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnome-shell is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'gnome-shell' has no installation candidate


--------
Everything else updates fine.

Thats all I know but I'm a bit nooby around the edges...

Any suggestions how to install this any other way?

---

### Post by Sketches on 2011-04-03
Pretty pls? Does anyone have an ulterior install method?

---

### Post by ankspo71 on 2011-04-04
Hi,
It looks to me that the repository URL is wrong. Click on the link you posted and look at the URL in your address bar. It has "testin" in the address, it should be "testing". So I would change the repository URL in your sources to point to the correct address and then try again. PPA repositories usually get added to the /etc/apt/sources.list.d/ directory, but if it isn't there, it will be in your /etc/apt/sources.list file.

Hope this helps.

---

### Post by Krytarik on 2011-04-04
+1 for fixing the URL. But, you can easily edit it via "System -> Administration -> Software Sources -> Other Software".

Greetings.

---

