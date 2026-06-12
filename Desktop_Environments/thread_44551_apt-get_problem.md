---
title: "apt-get problem"
date: 2005-06-26
forum: Desktop Environments
---

### Post by Frinkahedron on 2005-06-26
I'm trying to install Xmms so I do apt-get install Xmms. This happens:
```
root@ubuntu:/home/mark # sudo apt-get install Xmms
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list ftp://ftp.nerim.net stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list ftp://ftp.nerim.net testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

```

So I run apt-get update and this happens:
```
Fetched 74.1kB in 11s (6349B/s)
Failed to fetch ftp://ftp.nerim.net/debian-marillat/dists/stable/main/binary-i386/Packages.gz  MD5Sum mismatch
Failed to fetch ftp://ftp.nerim.net/debian-marillat/dists/testing/main/binary-i386/Packages.gz  MD5Sum mismatch
Reading package lists... Done
W: Couldn't stat source package list ftp://ftp.nerim.net stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list ftp://ftp.nerim.net testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used  instead.

```

Help?

---

### Post by TRAVISL on 2005-06-26
I had this same problem and solved it by removing all of the marillat sources from my apt-get list.   
```
sudo gedit /etc/apt/sources.list
```
Just run that and remove any non Ubuntu sources and run apt-get update and it should solve your problem.  Hope this helps.
Travis

---

### Post by Frinkahedron on 2005-06-26
so all you did was delete any lines that had marillat mentioned in them?

Want to be sure.

---

### Post by Frinkahedron on 2005-06-26
Okay, I removed the references, ran apt-get update and now this appears.

```
Reading package lists... Done
W: Duplicate sources.list entry http://us.archive.ubuntu.com hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
root@ubuntu:/home/mark #

```

EDIT: Upon running apt-get update again, it seems to have fixed it.

Thanks for your help.

---

### Post by TRAVISL on 2005-06-26
I'm glad it worked because I am still a newbie at this.  I would like to thank the forum for helping me with the same issue a few days ago.
Travis

---

