---
title: "VmWare installation Troubles"
date: 2006-10-24
forum: Desktop Environments
---

### Post by dolphin_1 on 2006-10-24
Having trouble installing my VmWare-Player onto 6.06 LTS.  I'm following directions in Ubuntu documentation per [https://help.ubuntu.com/community/InstallingVmPlayer](https://help.ubuntu.com/community/InstallingVmPlayer).

As advised, I checked kernel versions and they were different.  2.6.15-23 vs. 2.6.15-27. 

So I untared a downloaded version from the VmWare web site, and ran the install script:  ```
$ cd vmware-player-distrib/
$ sudo ./vmware-install.pl
```

The official docs say :
"Usually you can answer to all questions with the default answer (by typing enter), but it is always good idea to actually read all those questions before answering them."

This is where I run into trouble.  One of the questions ask:
"What is the location of the directory of C header files that match your running kernel?  [/usr/src/linux/include]"

The only directory I have under /usr/src is an rpm folder and it obviously isn't what the installer is looking for.

Also, along the way it wanted me to install gcc, the installation of which also failed.

Any ideas?

---

