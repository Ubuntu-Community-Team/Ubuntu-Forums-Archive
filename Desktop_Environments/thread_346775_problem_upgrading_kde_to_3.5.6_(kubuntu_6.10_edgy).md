---
title: "problem upgrading kde to 3.5.6 (kubuntu 6.10 edgy)"
date: 2007-01-26
forum: Desktop Environments
---

### Post by acope on 2007-01-26
Hi,

I'm trying to upgrade from kde 3.5.5 to 3.5.6:
[http://kubuntu.org/announcements/kde-356.php](http://kubuntu.org/announcements/kde-356.php)

But there's a problem with the **kdm** package:

> Preparing to replace kdm 4:3.5.5-0ubuntu3.2 (using .../kdm_4%3a3.5.6-0ubuntu1_i386.deb) ...
*** stack smashing detected ***: /usr/bin/perl terminated
dpkg: error processing /var/cache/apt/archives/kdm_4%3a3.5.6-0ubuntu1_i386.deb (--unpack):
 dpkg: warning - old pre-removal script killed by signal (Aborted)

*** stack smashing detected ***: /usr/bin/perl terminated
dpkg: error while cleaning up:
 subprocess post-installation script killed by signal (Aborted)


And now I'm stuck!

I've tried this:
> $ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies...Done
The following extra packages will be installed:
   kdm (3.5.6-0ubuntu1)
Suggested packages:
   menu (2.1.29)
The following packages will be upgraded:
   kdm (3.5.5-0ubuntu3.2 => 3.5.6-0ubuntu1)
1 upgraded, 0 newly installed, 0 to remove and 31 not upgraded.
103 not fully installed or removed.
Need to get 0B/642kB of archives.
After unpacking 28.7kB of additional disk space will be used.
Do you want to continue [Y/n]?
*** stack smashing detected ***: /usr/bin/perl terminated
Aborted
(Reading database ... 140996 files and directories currently installed.)
Preparing to replace kdm 4:3.5.5-0ubuntu3.2 (using .../kdm_4%3a3.5.6-0ubuntu1_i386.deb) ...
*** stack smashing detected ***: /usr/bin/perl terminated
dpkg: error processing /var/cache/apt/archives/kdm_4%3a3.5.6-0ubuntu1_i386.deb (--unpack):
 dpkg: warning - old pre-removal script killed by signal (Aborted)

*** stack smashing detected ***: /usr/bin/perl terminated
dpkg: error while cleaning up:
 subprocess post-installation script killed by signal (Aborted)
Errors were encountered while processing:
 /var/cache/apt/archives/kdm_4%3a3.5.6-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

and apt-get can't get past this problem.

Anyone seen this and knows how to resolve it?

---

### Post by acope on 2007-01-29
SOLVED:

Finally found that the problem goes away when DEBIAN_FRONTEND is set to "text"

i.e:

# export DEBIAN_FRONTEND=text
# apt-get ... (etc)


Don't know why, but that stopped the problem with "stack smashing detected".

:confused: 

But I'm happy that kde 3.5.6 is now installed!

---

### Post by chartman on 2007-04-20
Thanks for this.. I was completely lost. How did you get this idea???

---

