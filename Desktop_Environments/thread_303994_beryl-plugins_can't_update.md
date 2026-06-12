---
title: "beryl-plugins can't update"
date: 2006-11-21
forum: Desktop Environments
---

### Post by FuzZy2006 on 2006-11-21
i'm using trevino's svn beryl repositories, and when i try to update beryl plugins from version r1297 to r1336 it says:
```
 sudo apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  beryl-plugins beryl-plugins-data
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 2013kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://3v1n0.tuxfamily.org edgy/beryl-svn beryl-plugins-data 0.1.3+svn20061121-r1336-3v1ubuntu0 [1722kB]
Get:2 http://3v1n0.tuxfamily.org edgy/beryl-svn beryl-plugins 0.1.3+svn20061121-r1336-3v1ubuntu0 [291kB]
Fetched 2013kB in 18s (107kB/s)                                                
Failed to fetch http://3v1n0.tuxfamily.org/pool/edgy/beryl-svn/beryl-plugins-data_0.1.3+svn20061121-r1336-3v1ubuntu0_all.deb  Size mismatch
Failed to fetch http://3v1n0.tuxfamily.org/pool/edgy/beryl-svn/beryl-plugins_0.1.3+svn20061121-r1336-3v1ubuntu0_i386.deb  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

---

