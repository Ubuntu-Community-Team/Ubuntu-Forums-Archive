---
title: "Cannot install gnome Package 'gnome-shell' has no installation candidate"
date: 2012-03-06
forum: Desktop Environments
---

### Post by MaRiOsPWS on 2012-03-06
Hello,

I'm new in the forum and new in ubuntu in general (only worked with centos).

I've installed Ubuntu 11.04 (x86_64) on a vps and I want to install gnome.

I did try the instructions from the article [here]("http://techhamlet.com/2011/05/how-to-install-gnome-3-on-ubuntu-11-04/") but I have 2 problems

1st I cannot add gnome3 to the repository:

root@ubuntu:~# sudo add-apt-repository ppa:gnome3-team/gnome3
sudo: add-apt-repository: command not found

2nd it cannot find the package ...

root@ubuntu:~# sudo apt-get install gnome-shell
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package gnome-shell is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'gnome-shell' has no installation candidate

-Is this the correct way to install gnome?
-I read everywhere about gnome-shell is it the same thing is gnome ? 
-Any help to install gnome?

thank you.

---

### Post by MaRiOsPWS on 2012-03-06
It seems I've found the solution about the 1st problem:

root@ubuntu:~# sudo add-apt-repository ppa:gnome3-team/gnome3
sudo: add-apt-repository: command not found

Solution:

I had to run sudo apt-get install python-software-properties (needed for minimal Ubuntu Server installation)

but still I cannot install gnome:

root@ubuntu:~# sudo apt-get install gnome-shell
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package gnome-shell is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'gnome-shell' has no installation candidate

---

