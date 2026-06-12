---
title: "http://packages.ubuntu.com/hoary/"
date: 2005-06-25
forum: Desktop Environments
---

### Post by Dave_is_sexy on 2005-06-25
[http://packages.ubuntu.com/hoary/](http://packages.ubuntu.com/hoary/)

I wanna add this place as a repository! Things I need are there!

---

### Post by ow50 on 2005-06-25
No! It's not a repository, just a listing interface. The same packages are in the official ubuntu repositories. To get access to all the packages listed there, make sure you have all the repositories in your sources.list.

For example:
```
deb http://fi.archive.ubuntu.com/ubuntu/ hoary main universe multiverse restricted
deb http://fi.archive.ubuntu.com/ubuntu/ hoary-updates main universe multiverse restricted
deb http://security.ubuntu.com/ubuntu/ hoary-security main universe multiverse restricted
```
Just change the country code "fi" to suit your country, for example "us" for americans.

---

### Post by Dave_is_sexy on 2005-06-25
Ahhhhh

Everytime i add repositories i get this:

> W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hoary/multiverse Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hoary-updates/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hoary-updates/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_hoary-updates_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hoary-updates/multiverse Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_hoary-updates_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hoary-updates/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)

for everything regardless of what it is. you have to edit > reload packages! 
I nominate someone write that somewhere prominant

---

