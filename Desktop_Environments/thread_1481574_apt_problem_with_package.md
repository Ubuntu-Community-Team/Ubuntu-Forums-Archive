---
title: "apt: problem with package"
date: 2010-05-12
forum: Desktop Environments
---

### Post by thengineer on 2010-05-12
hello there!

first of: i couldn't find a category where my problem fits into, so please forgive me if its not in the right one.

resently i have installed a package (zapping) that could not be installed prober. and now when doing anything with apt, I get that error message about zapping. i've also tried to uninstall it, but that does fail as well. 
```

# apt-get remove zapping
Reading package lists... [...]
The following packages will be REMOVED:
  zapping
0 upgraded, 0 newly installed, 1 to remove and 66 not upgraded.
1 not fully installed or removed.
After this operation, 4,321kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 240074 files and directories currently installed.)
Removing zapping ...
dpkg (subprocess): unable to execute installed pre-removal script: Exec format error
dpkg: error processing zapping (--remove):
 subprocess installed pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 zapping
E: Sub-process /usr/bin/dpkg returned an error code (1)

```can anybody tell me how to get rid of that package?

thanks in advance, jakob

---

### Post by thengineer on 2010-05-12
okay. just solved that one by editing /var/lib/dpkg/status

---

