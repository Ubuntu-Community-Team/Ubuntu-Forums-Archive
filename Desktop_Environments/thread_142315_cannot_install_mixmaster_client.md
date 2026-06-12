---
title: "cannot install mixmaster client"
date: 2006-03-10
forum: Desktop Environments
---

### Post by lex1 on 2006-03-10
I installed the mixmaster client a weel ago but unistalled it a few days after
now when I try again it will not install.
useing sudo apt-get install mixmaster

Unpacking mixmaster (from .../mixmaster_3.0b2-1ubuntu1_i386.deb) ...
Setting up mixmaster (3.0b2-1ubuntu1) ...
mkdir: cannot create directory `/var/lib/mixmaster/Mix': No such file or directory
dpkg: error processing mixmaster (--configure):
subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
mixmaster
E: Sub-process /usr/bin/dpkg returned an error code (1)

lex1 :???:

---

### Post by astyanax on 2006-03-10
> Unpacking mixmaster (from .../mixmaster_3.0b2-1ubuntu1_i386.deb) ...
Setting up mixmaster (3.0b2-1ubuntu1) ...
mkdir: cannot create directory `/var/lib/mixmaster/Mix': No such file or directory


Have you looked to see if the /var/lib/mixmaster directory exists?  It looks like it's trying to create a directory in a directory that doesn't exist.  If it doesn't, do a:
sudo mkdir /var/lib/mixmaster

and then try installing again.

---

