---
title: "Where do I get  glibc-2.3.2.ds1-20ubuntu14 ??"
date: 2005-11-23
forum: Desktop Environments
---

### Post by Cud on 2005-11-23
I messed up my locales in a very complicated sequence of events that I can no longer entirely retrace, but involving other repositories...
The short of it is that in order to install locales again I need to install glibc-2.3.2.ds1-20ubuntu14 (or 13 ).
Where can I get this, and how do I install it?
I got glibc_2.3.2.ds1-20ubuntu14.diff.gz, but when I unpack it I get a "patch"
that I cant figure out how to run anyway..
Any Ideas on where to download glibc-2.3.2.ds1-20ubuntu14??
Thanks

Edit: When I try with apt-get I get the following error:

jesse@finally:~$ sudo apt-get -s install glibc-2.3.2.ds1-20ubuntu14
Reading package lists... Done
Building dependency tree... Done
Note, selecting libc6 instead of glibc-2.3.2.ds1-20ubuntu14
libc6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

I have libc6 2.3.2.ds1-22 installed 
So does that mean I need to downgrade libc6? How do I do that??
I thought that messing with libc6 is the proverbial  no-no..... (which I obvously already broke)
Thanks in advance.

SOLVED!! I installed this version of Locales: locales_2.3.2.ds1-22_all.deb

---

