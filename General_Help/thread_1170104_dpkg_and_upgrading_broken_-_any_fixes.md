---
title: "dpkg and upgrading broken - any fixes?"
date: 2009-05-25
forum: General Help
---

### Post by gotthardt on 2009-05-25
When trying to upgrade using symantic, command line, etc. I am told to use:
sudo dpkg --configure -a
to fix it. But using it, I get the following and I cannot upgrade or add any new packages: 

sudo dpkg --configure -a
Setting up libc6 (2.9-4ubuntu6) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Aborted
dpkg: subprocess post-installation script returned error exit status 134

I tried sudo dpkg -P libc6 and that let me run the --configure -a ok, but then it wants to install libc6 and I get the error again.

update: I worked a little further and its ldconfig that just aborts:
ldconfig -v
Aborted

-------------------------------------------------------------
FIX: I used strace (fortunately it was installed) and saw that ldconfig.real had a problem with opening the aux-cache in /var/cache/ldconfig   I deleted it and everything ran fine after that.
--------------------------------------------------------------


2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

9.04

---

