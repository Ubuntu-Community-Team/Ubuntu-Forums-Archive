---
title: "splitconfig.pl permissions"
date: 2008-03-25
forum: Desktop Environments
---

### Post by stetson123 on 2008-03-25
The following snippet of output shows that the permissions on debian/scripts/misc/splitconfig.pl  file  are incorrect.  I solved this by changing the permissions to allow executing as a program. This can be changed by right clicking on the file and choosing properties, then permissions and marking the the appropriate box. I suspect that this should be listed as a bug but I am only minutes old as a member and still ignorant of the bug process.

BTW, this is the desktop version i386, version 8.04

@rocketfish:~/linux-2.6.24$ debian/rules updateconfigs
dh_testdir
Processing i386 (i386) ... 
Running silentoldconfig for config.386 ... 
make[1]: Entering directory `/home/dad/linux-2.6.24'

SNIP

Running splitconfig.pl ... 

debian/scripts/misc/oldconfig: line 66: /home/dad/linux-2.6.24/debian/scripts/misc/splitconfig.pl: Permission denied
make: *** [updateconfigs] Error 1

---

