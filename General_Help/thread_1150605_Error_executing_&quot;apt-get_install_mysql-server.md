---
title: "Error executing &quot;apt-get install mysql-server&quot;"
date: 2009-05-06
forum: General Help
---

### Post by tirengarfio on 2009-05-06
Hi, im executing "sudo apt-get install mysql-server" and i get this error:


The following NEW packages will be installed:
  mysql-server mysql-server-5.0
0 upgraded, 2 newly installed, 0 to remove and 105 not upgraded.
Need to get 27.4MB/27.5MB of archives.
After this operation, 86.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main mysql-server-5.0 5.0.51a-3ubuntu5.4
  403 Forbidden [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main mysql-server-5.0 5.0.51a-3ubuntu5.4
  403 Forbidden [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-server-5.0_5.0.51a-3ubuntu5.4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-server-5.0_5.0.51a-3ubuntu5.4_i386.deb)  403 Forbidden [IP: 91.189.88.45 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

I run "apt-get update" but the error is the same. 

Is my fault or is not possible to download this package at this moment? If it is an error of the server, who should i contact?

Is there any way to know what repositories contain a concrete package?

Bye

---

