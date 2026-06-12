---
title: "When I open the advanced package manager I get the following errors"
date: 2006-02-19
forum: Desktop Environments
---

### Post by ade234uk on 2006-02-19
When I open the advanced package manager I get the following errors. This could also be the reason why Automatix is not working correctly and I cannot install third party codecs. How do I fix this problem?


W: Couldn't stat source package list [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages (/var/lib/apt/lists/wine.sourceforge.net_apt_binary_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by Stinger on 2006-02-19
I can confirm this !

Wine seems to have trouble , it goes awfully slow when I try to get wine 0.98.

It's even worse with "ftp//ftp.free.fr" the mirror  seem to be down at the moment I can't browse it using Firefox either.

Well my best guess would be that the mirror maintainers are looking at the problem right now , and that it will be fixed in near future.

---

### Post by ade234uk on 2006-02-20
I am glad I am not the only one. Hopefully they will come back soon.

ftp//ftp.free.fr is the server that contains the misc codecs for Automatix bloody typical. Its always the one you want lol.

I will wait.

---

