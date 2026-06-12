---
title: "Get Error When Updating Software On Ubuntu 18.04.4 LTS"
date: 2020-05-24
forum: Desktop Environments
---

### Post by lawrence-joy on 2020-05-24
To ready my system for an installation of a program I entered in my terminal 'sudo apt-get install python3 python3-dev python3-pip g++ make'. It asked me for my password of course and I answered yes when it said the system would use whatever amount of disk space. At the end I get the message "Errors were encountered while processing: mysql-server-5.7" and
"E: sub-process /usr/bin/dpkg returned an error code (1)"
I also have seen this when the automatic update takes place or when I did a manual update. What do I need to do?
--Thanks, Larry

---

### Post by westie457 on 2020-05-24
Hi, to give us a better understanding of the issue could you post the complete output of these terminal commands```
sudo apt update
sudo apt upgrade
```
Could you post the result in code tags it would be appreciated as this keeps the correct formatting and keeps 'smileys' away.
To generate the tags in an advanced reply hit the # symbol and paste the terminal output between the brackets.

---

### Post by lawrence-joy on 2020-05-24
Let me see if I can make this work. I went to Advanced Reply. Here goes.
```
larry@larry-MS-7693:~$ sudo apt update
[sudo] password for larry: 
Get:1 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]                                                     
Hit:2 http://ppa.launchpad.net/js-reynaud/kicad-5/ubuntu bionic InRelease                                                                  
Hit:3 http://mirror.lstn.net/mariadb/repo/10.4/ubuntu bionic InRelease                                         
Get:4 http://security.ubuntu.com/ubuntu bionic-security/main amd64 DEP-11 Metadata [40.6 kB]                        
Hit:5 http://ppa.launchpad.net/js-reynaud/kicad-5.1/ubuntu bionic InRelease                                                       
Get:6 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 DEP-11 Metadata [42.1 kB]                                                                         
Hit:7 http://ppa.launchpad.net/sicklylife/gnucash/ubuntu bionic InRelease                                                        
Get:8 http://security.ubuntu.com/ubuntu bionic-security/multiverse amd64 DEP-11 Metadata [2,464 B]                               
Hit:9 http://us.archive.ubuntu.com/ubuntu bionic InRelease                                                                                  
Get:10 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 DEP-11 Metadata [303 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 DEP-11 Metadata [273 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu bionic-updates/multiverse amd64 DEP-11 Metadata [2,468 B]
Get:15 http://us.archive.ubuntu.com/ubuntu bionic-backports/universe amd64 DEP-11 Metadata [7,972 B]
Err:16 http://mirror.1stn.net/mariadb/repo/10.4/ubuntu bionic InRelease                                                                                                                                    
  Could not resolve 'mirror.1stn.net'
Fetched 923 kB in 30s (30.7 kB/s) 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
W: Failed to fetch http://mirror.1stn.net/mariadb/repo/10.4/ubuntu/dists/bionic/InRelease  Could not resolve 'mirror.1stn.net'
W: Some index files failed to download. They have been ignored, or old ones used instead.

```
And ```
larry@larry-MS-7693:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libclang-common-7-dev libclang-common-8-dev libllvm7 libllvm8
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
Setting up mysql-server-5.7 (5.7.30-0ubuntu0.18.04.1) ...
/var/lib/dpkg/info/mysql-server-5.7.postinst: line 191: /usr/share/mysql-common/configure-symlinks: No such file or directory
dpkg: error processing package mysql-server-5.7 (--configure):
 installed mysql-server-5.7 package post-installation script subprocess returned error exit status 127
Errors were encountered while processing:
 mysql-server-5.7
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
So there you go. Hope you can help me out.
--Larry

---

### Post by deadflowr on 2020-05-25
Bad mariadb mirror.
Change it to another.
You can check for mirrors here:
[https://downloads.mariadb.org/mariadb/repositories/#distro=Ubuntu&distro_release=bionic--ubuntu_bionic&mirror=mva&version=10.4]("https://downloads.mariadb.org/mariadb/repositories/#distro=Ubuntu&distro_release=bionic--ubuntu_bionic&mirror=mva&version=10.4")

I'd simply find a mirror and edit the source entry to fit it.
[https://help.ubuntu.com/community/Repositories/CommandLine]("https://help.ubuntu.com/community/Repositories/CommandLine")

---

