---
title: "failed to fetch error while installing mysql server db in ubuntu"
date: 2009-07-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vivek_gorade on 2009-07-06
I am trying to install mysql database on ubuntu. Below is the log of activities and error I need to deal with-

vivek@vivek-laptop:/$ sudo apt-get install mysql-server
[sudo] password for vivek:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libdbd-mysql-perl libdbi-perl libmysqlclient15off mysql-client-5.0
  mysql-common mysql-server-5.0
Suggested packages:
  dbishell mysql-doc-5.0 tinyca
Recommended packages:
  mailx
The following NEW packages will be installed:
  libdbd-mysql-perl libdbi-perl libmysqlclient15off mysql-client-5.0
  mysql-common mysql-server mysql-server-5.0
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 37.2MB of archives.
After unpacking 109MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  mysql-common libdbi-perl libmysqlclient15off libdbd-mysql-perl
  mysql-client-5.0 mysql-server-5.0 mysql-server
Install these packages without verification [y/N]? y
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main mysql-common 5.0.45-1ubuntu3  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main libdbi-perl 1.57-1
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main libmysqlclient15off 5.0.45-1ubuntu3
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main libdbd-mysql-perl 4.004-2
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main mysql-client-5.0 5.0.45-1ubuntu3
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main mysql-server-5.0 5.0.45-1ubuntu3
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main mysql-server 5.0.45-1ubuntu3
  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-common_5.0.45-1ubuntu3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-common_5.0.45-1ubuntu3_all.deb)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libd/libdbi-perl/libdbi-perl_1.57-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libd/libdbi-perl/libdbi-perl_1.57-1_i386.deb)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/libmysqlclient15off_5.0.45-1ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/libmysqlclient15off_5.0.45-1ubuntu3_i386.deb)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libd/libdbd-mysql-perl/libdbd-mysql-perl_4.004-2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libd/libdbd-mysql-perl/libdbd-mysql-perl_4.004-2_i386.deb)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-client-5.0_5.0.45-1ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-client-5.0_5.0.45-1ubuntu3_i386.deb)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-server-5.0_5.0.45-1ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-server-5.0_5.0.45-1ubuntu3_i386.deb)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-server_5.0.45-1ubuntu3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-server_5.0.45-1ubuntu3_all.deb)  404 Not Found [IP: 91.189.88.40 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


Right now I am in process of upgrading ubuntu from 7.10 to 8.04 LTS version to see if that makes any difference. If it does, I will surely come back to this post and update everybody. Until that happens, any pointers are welcome.

---

### Post by vivek_gorade on 2009-07-26
Problem is resolved. It was with the old version of Ubuntu - Gitsey Gibon. I upgraded to  Ubuntu 8.04 - the Hardy Heron and mysql setup using apt-get was a cakewalk.

---

