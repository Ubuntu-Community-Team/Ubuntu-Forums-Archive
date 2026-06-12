---
title: "synaptic"
date: 2005-04-25
forum: Desktop Environments
---

### Post by sanman_nor on 2005-04-25
I wanted to play avi so I fallowed the directions in the unofficial guid 
and now when I starte synaptic I get this error


W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages)
what does this mean and how do I fix it

---

### Post by heimo on 2005-04-25
Check your /etc/apt/sources.list for duplicate repositories. Try running *apt-get clean; apt-get update *on terminal and try again. If that doesn't help, please post your sources.list file

---

### Post by sanman_nor on 2005-04-25
that did not fix it, but I then found the duplicite repositorys when opening the repositorys list 
thanks

---

