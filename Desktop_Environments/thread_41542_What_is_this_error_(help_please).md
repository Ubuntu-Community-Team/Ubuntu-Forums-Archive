---
title: "What is this error? (help please)"
date: 2005-06-13
forum: Desktop Environments
---

### Post by Kapre on 2005-06-13
Hiyall,

Could someone please help me on the error I've been getting when I run Ubuntu update? The error : 

Could not download all repository indexes - the repository might be no longer available or could not be contacted because of network problems. If available an older version of the indes will be used. Otherwise repository will be ignored. Check your network connection:
[ftp://ftp.nerim.net/debian-marillat/dists/stable/main/binary-i386/Packages.gz:](ftp://ftp.nerim.net/debian-marillat/dists/stable/main/binary-i386/Packages.gz:) MD5Sum mismatch
[ftp://ftp.nerim.net/debian-marillat/dists/testing/main/binary-i386/Packages.gz:](ftp://ftp.nerim.net/debian-marillat/dists/testing/main/binary-i386/Packages.gz:) MD5Sum mismatch

After this comes:

W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-i386_Packages) - stat (2 No such file or directory)

Then:

W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-i386_Packages) - stat (2 No such file or directory)

Then:

This thing on mozilla-firefox and mozilla-firefox-gnome support comes up saying It is not possible to upgrade all packages and I should try to use Synaptic "Smart Upgrade". But when I go to Synaptic and mark this mozilla (ffox and gnome support) it says :

Some of the packages could not be retrieved from the server. Do you want to continue, ignoring this packages? If I choose Yes, it will just say, Changes Applied then this error:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo1_0.3.0-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo1_0.3.0-1_i386.deb)
  MD5Sum mismatch

I need your help because I dont know if this errors are critical or should I just continue ignoring them.

Kapre   ](*,)

---

### Post by aysiu on 2005-06-13
Why is nerim in there? Are you using Debian repositories with Ubuntu? Ubuntu has its own repositories.

---

