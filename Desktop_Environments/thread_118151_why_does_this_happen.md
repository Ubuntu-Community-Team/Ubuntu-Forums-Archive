---
title: "why does this happen"
date: 2006-01-16
forum: Desktop Environments
---

### Post by ESPOiG on 2006-01-16
wen i try to install a program... this is just an expample but it happend wen i tried to install apache2 ?

ross@LaptopUbuntu:~$ sudo apt-get install firefox
Password:
Reading package lists... Done
Building dependency tree... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 62 not upgraded.
W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) breezy/free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) breezy/non-free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

---

### Post by GeneralZod on 2006-01-16
Try

```

sudo apt-get update

```

---

### Post by Gustav on 2006-01-16
Those are unofficial mirrors - they might be down?

---

### Post by ESPOiG on 2006-01-16
i have tried update and it dont work and wen it was happenin with apache my friends  tried it on his (install apache that is) and he had no probs

---

### Post by nocturn on 2006-01-16
The mirrormax backport repos have been closed

---

### Post by ShaneAu on 2006-01-18
[QUOTE=nocturn]The mirrormax backport repos have been closed[/QUOTE]

breezy-extras is ok to have in there.

apt-get update should fix it. And as you can see the problem isn't only with MirrorMAX. :)

---

