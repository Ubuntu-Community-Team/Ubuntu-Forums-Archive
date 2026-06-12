---
title: "apt-get update problems (error messages included)"
date: 2005-06-12
forum: Desktop Environments
---

### Post by minimidgy on 2005-06-12
every time I try to run sudo apt-get update, I get messages such as these:

W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

I also get error messages every time I try to install a program.

---

### Post by Xian on 2005-06-12
It's not a local problem. You might want to just disable those nerim.net repos for the time being, as they apparently are causing some issues at the momment.

---

