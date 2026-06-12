---
title: "apt-get problems, hang on language-pack-en-base package"
date: 2009-02-19
forum: General Help
---

### Post by kain2396 on 2009-02-19
Every time I try to install anything, apt-get attempts to get the language-pack-en-base package, and then nothing happens, I'm stuck here:

```
kain@IESFnet:~$ sudo apt-get install subversion
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libapr1 libaprutil1 libneon27-gnutls libsvn1
Suggested packages:
  subversion-tools db4.6-util
The following NEW packages will be installed:
  libapr1 libaprutil1 libneon27-gnutls libsvn1 subversion
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
90 not fully installed or removed.
Need to get 1462kB of archives.
After this operation, 6943kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com intrepid/main libapr1 1.2.12-4 [114kB]
Get:2 http://us.archive.ubuntu.com intrepid/main libaprutil1 1.2.12+dfsg-7 [82.3kB]
Get:3 http://us.archive.ubuntu.com intrepid/main libneon27-gnutls 0.28.2-2build1 [119kB]
Get:4 http://us.archive.ubuntu.com intrepid/main libsvn1 1.5.1dfsg1-1ubuntu2 [794kB]
Get:5 http://us.archive.ubuntu.com intrepid/main subversion 1.5.1dfsg1-1ubuntu2 [353kB]
Fetched 1462kB in 5s (274kB/s)     
Selecting previously deselected package libapr1.
(Reading database ... 131833 files and directories currently installed.)
Unpacking libapr1 (from .../libapr1_1.2.12-4_amd64.deb) ...
Selecting previously deselected package libaprutil1.
Unpacking libaprutil1 (from .../libaprutil1_1.2.12+dfsg-7_amd64.deb) ...
Selecting previously deselected package libneon27-gnutls.
Unpacking libneon27-gnutls (from .../libneon27-gnutls_0.28.2-2build1_amd64.deb) ...
Selecting previously deselected package libsvn1.
Unpacking libsvn1 (from .../libsvn1_1.5.1dfsg1-1ubuntu2_amd64.deb) ...
Selecting previously deselected package subversion.
Unpacking subversion (from .../subversion_1.5.1dfsg1-1ubuntu2_amd64.deb) ...
Processing triggers for man-db ...
Setting up language-pack-en-base (1:8.10+20081107) ...
Generating locales...
  en_AU.UTF-8... up-to-date
  en_BW.UTF-8... up-to-date
  en_CA.UTF-8... up-to-date
  en_DK.UTF-8... up-to-date
  en_GB.UTF-8... 

```

---

### Post by kain2396 on 2009-02-19
Problem resolved.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/249340](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/249340)

The upshot is that you have to exit the X session, bring up a terminal from the login screen, do a dpkg --configure -a and then return to the session and restart the install.

---

