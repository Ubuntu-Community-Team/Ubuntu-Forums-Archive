---
title: "Can't apt-get install portmap or nfs-common on 8.04.1"
date: 2008-09-29
forum: Desktop Environments
---

### Post by hqic on 2008-09-29
I'm trying to add nfs client to my Ubuntu desktop.  Reading through various forums and sites, including this site (which specifically calls out 8.04):

[http://www.howtoforge.com/perfect-nfs-on-ubuntu-8.04-amd64](http://www.howtoforge.com/perfect-nfs-on-ubuntu-8.04-amd64)

I have come to understand that I must install nfs-common using:

*sudo apt-get install portmap nfs-common*

I did just that on a 7.10 desktop Ubuntu and it worked perfectly.  

However, I can't install the packages on a freshly installed Ubuntu 8.04.1 desktop.  Separating out the two attempts, I get:

[I]$ sudo apt-get install nfs-common
Reading package lists... Done
Building dependency tree      
Reading state information... Done
Package nfs-common is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package nfs-common has no installation candidate[/I]


[I]$ sudo apt-get install portmap
Reading package lists... Done
Building dependency tree      
Reading state information... Done
E: Couldn't find package portmap[/I]

Searching the forums, I can't find any reference to this issue, but find frequent occurrence of normal operation getting these packages, so I assume I have something wrong on my end.

Any help?

---

