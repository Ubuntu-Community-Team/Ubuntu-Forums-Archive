---
title: "Error: apt-get install debootstrap"
date: 2009-01-12
forum: General Help
---

### Post by sula230 on 2009-01-12
Hi ALL,
This is my first thread..

I have the following error:

**#apt-get install debootstrap**
[COLOR="DarkRed"]Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  debootstrap
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 50.7kB of archives.
After this operation, 266kB of additional disk space will be used.
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main debootstrap 1.0.10
  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/d/debootstrap/debootstrap_1.0.10_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/debootstrap/debootstrap_1.0.10_all.deb)  Could not resolve 'archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing[/COLOR]?


Any ideas about solving this problem?!

---

### Post by ajgreeny on 2009-01-12
Firstly try ```
sudo apt-get update
``` in terminal and then perhaps try ```
sudo apt-get install -f
``` to see if you have any broken packages.  It doesn't look like you do, but this will do no harm.  Also let's see a copy of your /etc/apt/sources.list file to see if there is anything obviously wrong with that, which I think is the most likely reason for the problem.  It may be that simply commenting out the url line noted in your error message will solve the problem as debootstrap seems to be in the main repos

---

