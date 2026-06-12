---
title: "update problem"
date: 2006-02-15
forum: Desktop Environments
---

### Post by Micro Rotors on 2006-02-15
Ok I just tried to update breezy and I got this output;

[PHP]bill@Linux:~$ sudo apt-get update
Get:1 http://security.ubuntu.com breezy-security Release.gpg [189B]
Get:2 http://archive.ubuntu.com breezy Release.gpg [189B]
Get:3 http://archive.ubuntu.com breezy-updates Release.gpg [189B]
Hit http://security.ubuntu.com breezy-security Release
Get:4 http://archive.ubuntu.com breezy-backports Release.gpg [189B]
Hit http://archive.ubuntu.com breezy Release
Get:5 http://archive.ubuntu.com breezy-updates Release [30.9kB]
Hit http://security.ubuntu.com breezy-security/main Packages
Hit http://security.ubuntu.com breezy-security/restricted Packages
Hit http://security.ubuntu.com breezy-security/main Sources
Hit http://security.ubuntu.com breezy-security/restricted Sources
Hit http://security.ubuntu.com breezy-security/universe Packages
Hit http://security.ubuntu.com breezy-security/universe Sources
Get:6 http://archive.ubuntu.com breezy-backports Release [19.6kB]
Hit http://archive.ubuntu.com breezy/main Sources
Hit http://archive.ubuntu.com breezy/restricted Sources
Hit http://archive.ubuntu.com breezy/main Packages
Hit http://archive.ubuntu.com breezy/restricted Packages
Hit http://archive.ubuntu.com breezy/main Sources
Hit http://archive.ubuntu.com breezy/restricted Sources
Hit http://archive.ubuntu.com breezy/universe Packages
Hit http://archive.ubuntu.com breezy/universe Sources
Hit http://archive.ubuntu.com breezy/multiverse Packages
Hit http://archive.ubuntu.com breezy/multiverse Sources
Get:7 http://archive.ubuntu.com breezy-updates/main Packages [31.3kB]
Get:8 http://archive.ubuntu.com breezy-updates/restricted Packages [14B]
Get:9 http://archive.ubuntu.com breezy-updates/main Packages [31.3kB]
83% [7 Packages bzip2 0] [9 Packages 3785/31.3kB 12%]
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://archive.ubuntu.com breezy-updates/main Packages
  Sub-process bzip2 returned an error code (2)
Get:10 http://archive.ubuntu.com breezy-updates/restricted Packages [14B]
Get:11 http://archive.ubuntu.com breezy-updates/main Sources [15.8kB]
Get:12 http://archive.ubuntu.com breezy-updates/restricted Sources [14B]
Get:13 http://archive.ubuntu.com breezy-backports/main Packages [14.0kB]
Get:14 http://archive.ubuntu.com breezy-backports/restricted Packages [14B]
Get:15 http://archive.ubuntu.com breezy-backports/universe Packages [26.1kB]
Get:16 http://archive.ubuntu.com breezy-backports/multiverse Packages [1353B]
Fetched 171kB in 2s (68.0kB/s)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz  Sub-process bzip2 returned an error code (2)
Reading package lists... Done
W: Duplicate sources.list entry http://archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
bill@Linux:~$

[/PHP]What the heck is this?

---

### Post by dcstar on 2006-02-15
[QUOTE=Micro Rotors]Ok I just tried to update breezy and I got this output;
......
What the heck is this?[/QUOTE]
Possible network/repository problem, try again.

---

### Post by Micro Rotors on 2006-02-15
Same thing, it's been doing this since monday.

---

