---
title: "smbfs - dependency error"
date: 2006-07-30
forum: Desktop Environments
---

### Post by mudra on 2006-07-30
I am trying to follow the guide (Ubuntu 6.06 starter guide) to allow smbfs to mount network shares; but when I try to install smbfs I get the following error.

> root@UBUNTUM:~# apt-get install smbfs
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  smbfs: Depends: samba-common (= 3.0.14a-6ubuntu1.1) but 3.0.22-1ubuntu3.1 is to be installed
E: Broken packages


Anyone have any ideas ?

I have tried an apt-get update, but this does not seem to cure the problem.

I am more than happy to give anymore information.

Mudra

---

### Post by bullgr on 2006-07-30
hi...

fist of all try this to install samba

> sudo apt-get update

to update the dependency list

> sudo apt-get install samba

and then

> sudo apt-get install smbfs

to install samba

i don't know if you have installed samba and cannot just install smbfs
if so, try to comment the lines in /etc/apt/sources.list all the dependencies of backports, universe and multiverse and try again the steps i wrote above.

hope i help... :D

---

### Post by mudra on 2006-07-30
Thankyou so much, the removal of the repostitries, did the trick.

:smile:

---

