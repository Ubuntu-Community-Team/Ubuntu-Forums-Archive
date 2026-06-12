---
title: "Error messages in synaptec"
date: 2005-10-07
forum: Desktop Environments
---

### Post by dizbah on 2005-10-07
I am getting the following error when trying to remove or add anything in synnaptec.  Can anyone assist me please?

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/wine_0.0.20050419-1~5.04ubp1_i386.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/wine_0.0.20050419-1~5.04ubp1_i386.deb)
  404 Not Found


W: Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/wine-utils_0.0.20050419-1~5.04ubp1_i386.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/wine-utils_0.0.20050419-1~5.04ubp1_i386.deb)
  404 Not Found

---

### Post by Ampersand on 2005-10-07
Most of those can be solved using the Reload button in synaptic. 

[http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) is no longer used, instructions for adding the working repository can be found here: [https://wiki.ubuntu.com/UbuntuBackports](https://wiki.ubuntu.com/UbuntuBackports)

---

### Post by KingBahamut on 2005-10-07
Remove your backports repos, the mirrormax ones dont work / are down. 

I dont see whats wrong with the first one, but try an update again. 

Ampersand, you got the backports link handy?

---

