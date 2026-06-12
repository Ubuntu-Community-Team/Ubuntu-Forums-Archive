---
title: "dpkg error with &quot;apt-get update&quot;"
date: 2009-01-05
forum: General Help
---

### Post by Bllz on 2009-01-05
Hello fellow 'buntu-ers!  I'm currently out of the country and attempting to keep my home server running via ssh.  So far no problems except that I'm getting a weird dpkg error when I try to "sudo apt-get update && sudo apt-get upgrade"

Full output is as follows:
```
sudolouis@server:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for louis:
Hit http://archive.ubuntu.com hardy Release.gpg
Ign http://archive.ubuntu.com hardy/main Translation-en_US
Hit http://packages.medibuntu.org hardy Release.gpg
Ign http://archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://archive.ubuntu.com hardy/universe Translation-en_US
Ign http://archive.ubuntu.com hardy/multiverse Translation-en_US
Get:1 http://archive.ubuntu.com hardy-updates Release.gpg [189B]
Ign http://archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://archive.ubuntu.com hardy-security Release.gpg
Ign http://archive.ubuntu.com hardy-security/main Translation-en_US
Ign http://archive.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://archive.ubuntu.com hardy-security/universe Translation-en_US
Ign http://archive.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://archive.ubuntu.com hardy-backports Release.gpg
Ign http://packages.medibuntu.org hardy/free Translation-en_US
Ign http://archive.ubuntu.com hardy-backports/main Translation-en_US
Ign http://archive.ubuntu.com hardy-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com hardy-backports/universe Translation-en_US
Ign http://archive.ubuntu.com hardy-backports/multiverse Translation-en_US
Hit http://archive.ubuntu.com hardy Release
Get:2 http://archive.ubuntu.com hardy-updates Release [58.5kB]
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US
Hit http://archive.ubuntu.com hardy-security Release
Hit http://archive.ubuntu.com hardy-backports Release
Hit http://packages.medibuntu.org hardy Release
Hit http://archive.ubuntu.com hardy/main Packages
Hit http://archive.ubuntu.com hardy/restricted Packages
Hit http://archive.ubuntu.com hardy/universe Packages
Hit http://archive.ubuntu.com hardy/multiverse Packages
Hit http://archive.ubuntu.com hardy/universe Sources
Hit http://archive.ubuntu.com hardy/multiverse Sources
Hit http://archive.ubuntu.com hardy/main Sources
Hit http://archive.ubuntu.com hardy/restricted Sources
Get:3 http://archive.ubuntu.com hardy-updates/main Packages [402kB]
Hit http://packages.medibuntu.org hardy/free Packages
Hit http://packages.medibuntu.org hardy/non-free Packages
Get:4 http://archive.ubuntu.com hardy-updates/restricted Packages [7487B]
Get:5 http://archive.ubuntu.com hardy-updates/universe Packages [149kB]
Get:6 http://archive.ubuntu.com hardy-updates/multiverse Packages [24.8kB]
Get:7 http://archive.ubuntu.com hardy-updates/main Sources [104kB]
Get:8 http://archive.ubuntu.com hardy-updates/restricted Sources [892B]
Get:9 http://archive.ubuntu.com hardy-updates/universe Sources [34.5kB]
Get:10 http://archive.ubuntu.com hardy-updates/multiverse Sources [4159B]
Hit http://archive.ubuntu.com hardy-security/main Packages
Hit http://archive.ubuntu.com hardy-security/restricted Packages
Hit http://archive.ubuntu.com hardy-security/universe Packages
Hit http://archive.ubuntu.com hardy-security/multiverse Packages
Hit http://archive.ubuntu.com hardy-security/main Sources
Hit http://archive.ubuntu.com hardy-security/restricted Sources
Hit http://archive.ubuntu.com hardy-security/universe Sources
Hit http://archive.ubuntu.com hardy-security/multiverse Sources
Hit http://archive.ubuntu.com hardy-backports/main Packages
Hit http://archive.ubuntu.com hardy-backports/restricted Packages
Hit http://archive.ubuntu.com hardy-backports/universe Packages
Hit http://archive.ubuntu.com hardy-backports/multiverse Packages
Hit http://archive.ubuntu.com hardy-backports/main Sources
Hit http://archive.ubuntu.com hardy-backports/restricted Sources
Hit http://archive.ubuntu.com hardy-backports/universe Sources
Hit http://archive.ubuntu.com hardy-backports/multiverse Sources
Fetched 786kB in 2s (311kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  libnm-util0 network-manager xserver-xorg-video-geode
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 189kB/336kB of archives.
After this operation, 4096B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com hardy-updates/main libnm-util0 0.6.6-0ubuntu5.8.04.1 [33.5kB]
Get:2 http://archive.ubuntu.com hardy-updates/main network-manager 0.6.6-0ubuntu5.8.04.1 [156kB]
Fetched 189kB in 0s (247kB/s)
dpkg: parse error, in file `/var/lib/dpkg/status' near line 23194 package `libapr1':
 duplicate value for user-defined field `Original-Maintainer'
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by sisco311 on 2009-01-05
try:
```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo aptitude update
```

---

### Post by Bllz on 2009-01-05
> **sisco311 said:**
> try:
```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo aptitude update
```

Thanks for the reply!  May I just ask what this does?  It's not that I don't trust you, but I just like to know what something does (especially when there's a 'sudo' prefix).

Thanks!

---

### Post by blazemore on 2009-01-05
Would you please type in
```
cat /etc/apt/sources.list
```
This displays the contents of the file sources.list

Please paste the results here.

---

### Post by sisco311 on 2009-01-05
> dpkg: parse error, in file `/var/lib/dpkg/status' near line 23194 package `libapr1':
 duplicate value for user-defined field `Original-Maintainer

According to the error message the /var/lib/dpkg/status file is corrupted. The system stores a backup of this file (/var/lib/dpkg/status-old).

The cp (copy) command will replace the corrupted file with the backup.

---

### Post by blazemore on 2009-01-05
```
sudo rm -rfv /var/lib/dpkg/status && sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

---

