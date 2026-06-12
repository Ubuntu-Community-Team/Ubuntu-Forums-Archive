---
title: "Waiting for headers... forever"
date: 2005-12-18
forum: Desktop Environments
---

### Post by GabrielWolff on 2005-12-18
While trying to install wine, I got the following output:

gabriel@ubuntu:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  wine
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 13.8MB of archives.
After unpacking 205kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  wine
Install these packages without verification [y/N]? y
0% [Waiting for headers]

This is where it stops - forever. While writing this it STILL waits for the headers.

Why's that, and what's a header anyway?

Thanx

Gabriel

---

### Post by Peter76 on 2005-12-18
Hello, apparantly the wine servers are quite slow, upgraded it a couple of days ago, and the download broke a couple of times due to slow speed. Just keep trying. A header is ( normally ) a file which declares functions of a library used in compiling and programming with that library. Good luck

---

