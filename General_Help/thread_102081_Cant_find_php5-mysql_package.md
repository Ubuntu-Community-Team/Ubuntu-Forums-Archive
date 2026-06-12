---
title: "Cant find php5-mysql package"
date: 2005-12-11
forum: General Help
---

### Post by TFleck on 2005-12-11
Im getting some erros while updating the apt-get lists. The only repositories I use are the original ones (main, universe, backports, security, etc).
Do you know some repositories where I can find  php5-mysql package ?

---

### Post by ape on 2005-12-11
What errors are you getting. I'm seeing that the php5-mysql package is getting installed from the main breezy repository.  Running `apt-get -s install php5-mysql` results in the following output on my machine:

Reading package lists...
Building dependency tree...
The following extra packages will be installed:
  apache2-common apache2-mpm-prefork apache2-utils libapache2-mod-php5
  php5-common ssl-cert
Suggested packages:
  apache2-doc php-pear
The following NEW packages will be installed:
  apache2-common apache2-mpm-prefork apache2-utils libapache2-mod-php5
  php5-common php5-mysql ssl-cert
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.

---

### Post by TFleck on 2005-12-11
Its an error with the repositories. Im getting errors when trying to update the repositories.

when I run apt-get install -s php5-mysql, i get this:

```
Reading package lists... Done
Building dependency tree... Done
Package php5-mysql is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list http://br.archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/br.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://br.archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/br.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package php5-mysql has no installation candidate

```

---

### Post by ape on 2005-12-12
do you get the same error if you try a different repository in your /etc/apt/sources.list?  I'm using the following:

[FONT="Courier New"]deb [http://ubuntu.cs.utah.edu/ubuntu](http://ubuntu.cs.utah.edu/ubuntu) breezy main restricted universe multiverse
deb-src [http://ubuntu.cs.utah.edu/ubuntu](http://ubuntu.cs.utah.edu/ubuntu) breezy main restricted universe multiverse

deb [http://ubuntu.cs.utah.edu/ubuntu](http://ubuntu.cs.utah.edu/ubuntu) breezy-security main restricted universe multiverse
deb-src [http://ubuntu.cs.utah.edu/ubuntu](http://ubuntu.cs.utah.edu/ubuntu) breezy-security main restricted universe multiverse[/FONT]

---

