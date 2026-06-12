---
title: "apt connection problems"
date: 2005-12-17
forum: General Help
---

### Post by zvodd on 2005-12-17
I have just installed Kubuntu the other day. And i have been trying to set up a LAMP so i can test my PHP scripts on it. But when i try to use apt it always display messages like file not found or it shows the host's IP address as 1.0.0.0. I actually did manage to connect yesterday and get most of the recomended updates but now i am getting these errors again:

```

zvodd@zoidberg:~$ apt-cache search game
libxxf86dga1 - X11 Direct Graphics Access extension library
W: Couldn't stat source package list http://au.archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://au.archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://au.archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://au.archive.ubuntu.com breezy/multiverse Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://au.archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://au.archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://au.archive.ubuntu.com breezy-updates/universe Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-updates_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://au.archive.ubuntu.com breezy-updates/multiverse Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-updates_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list ftp://cipherfunk.org breezy/main Packages (/var/lib/apt/lists/cipherfunk.org_pub_packages_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)

```
Now, these errors and the bad IP address error have led me to believe it was a networking error. So i quickly did a ping to one of the hosts:
```

zvodd@zoidberg:~$ ping au.archive.ubuntu.com
PING au.archive.ubuntu.com (130.95.3.26) 56(84) bytes of data.
64 bytes from au.archive.ubuntu.com (130.95.3.26): icmp_seq=1 ttl=57 time=15.8 ms
64 bytes from au.archive.ubuntu.com (130.95.3.26): icmp_seq=2 ttl=57 time=15.5 ms
64 bytes from au.archive.ubuntu.com (130.95.3.26): icmp_seq=3 ttl=57 time=15.9 ms
--- au.archive.ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 15.584/15.804/15.991/0.167 ms

```
As you can see there doesn't seem to be any network connectivity problem, at least on the lower layers.
I am out of ideas, and i have no idea how come i got it working for a short period yesterday (i also used adept, same problem, but worked for the short time too). 
Any help would be appreciated.

---

### Post by zvodd on 2005-12-17
Oops, I posted this in the wrong forum, sorry about that. Can one of the mods move it please?

---

### Post by Imexius on 2006-01-05
This seems to be a problem with the site your downloading form, change the "au" part to "ca" in your repositories and see what happens.

---

