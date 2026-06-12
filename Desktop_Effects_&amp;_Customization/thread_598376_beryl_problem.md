---
title: "beryl problem"
date: 2007-10-31
forum: Desktop Effects &amp; Customization
---

### Post by alantary on 2007-10-31
Hello All I'm new to linux, and I try ubuntu 7.10 and I find it amazing but i have some errors like :

1.  sudo apt-get update
Failed to fetch [http://jo.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.bz2](http://jo.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.bz2)  Hash Sum mismatch
Failed to fetch [http://jo.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.bz2](http://jo.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.bz2)  Hash Sum mismatch
Reading package lists... Done
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

2. sudo apt-get install beryl emerald-themes
Failed to fetch [http://ubuntu.beryl-project.org/pool/feisty/main/0.2.0/beryl-plugins-data_0.2.0~0beryl1_all.deb](http://ubuntu.beryl-project.org/pool/feisty/main/0.2.0/beryl-plugins-data_0.2.0~0beryl1_all.deb)  Size mismatch
Failed to fetch [http://ubuntu.beryl-project.org/pool/feisty/main/0.2.0/emerald-themes_0.2.0~0beryl1_all.deb](http://ubuntu.beryl-project.org/pool/feisty/main/0.2.0/emerald-themes_0.2.0~0beryl1_all.deb)  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Any help please ... I followed all the instruction in this page:
[http://onlyubuntu.blogspot.com/2007/03/how-to-install-beryl-with-latest-nvidia.html](http://onlyubuntu.blogspot.com/2007/03/how-to-install-beryl-with-latest-nvidia.html)
:(

---

### Post by Maestro23 on 2007-10-31
First off, Beryl is no more.  Compiz-Fusion has taken its place.
[http://www.compiz-fusion.org/](http://www.compiz-fusion.org/)

How to install in 7.10: [https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

Second: Can you post your /etc/apt/sources.list

In a terminal:

> cat /etc/apt/sources.list

Copy/Paste output here.

---

