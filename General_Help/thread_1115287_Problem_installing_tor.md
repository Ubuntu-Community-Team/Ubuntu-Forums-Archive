---
title: "Problem installing tor"
date: 2009-04-03
forum: General Help
---

### Post by ShaunG on 2009-04-03
Hey guys,

I am hoping someone will be able to help me with the following. 

I am trying to install tor and have followed the instruction on their site and added the necessary lines to /etc/apt/sources.list but when I attempt to install tor I get the following in my console.

> The following NEW packages will be installed:
  tor
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1215kB of archives.
After this operation, 2601kB of additional disk space will be used.
Get:1 [http://mirror.noreply.org](http://mirror.noreply.org) hardy/main tor 0.2.0.34-1~hardy+1 [1215kB]
Fetched 1215kB in 34s (34.9kB/s)                                                   
Selecting previously deselected package tor.
(Reading database ... 261226 files and directories currently installed.)
Unpacking tor (from .../tor_0.2.0.34-1~hardy+1_i386.deb) ...
Setting up tor (0.2.0.34-1~hardy+1) ...
Raising maximum number of filedescriptors (ulimit -n) to 32768.
Starting tor daemon: tor...
ABORTED: Tor configuration invalid:
Apr 03 22:11:06.619 [notice] Tor v0.2.0.34 (r18423). This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Apr 03 22:11:06.621 [warn] Cannot seed RNG -- no entropy source found.
Apr 03 22:11:06.621 [err] tor_init(): Bug: Unable to seed random number generator. Exiting.
invoke-rc.d: initscript tor, action "start" failed.
dpkg: error processing tor (--configure):
 subprocess post-installation script returned error exit status 255
Errors were encountered while processing:
 tor
E: Sub-process /usr/bin/dpkg returned an error code (1)


Then if I attempt to remove tor I get the following

> graysr@archimedes:~$ sudo apt-get remove tor
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  tor
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 2601kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 261316 files and directories currently installed.)
Removing tor ...
Stopping tor daemon: not running (there is no /var/run/tor/tor.pid).


I am wondering if there is possibly a problem within /var/run?

Any help with this is greatly appreciated,

Thanks.

~Shaun

---

### Post by oldos2er on 2009-04-03
Is there some reason you're not installing tor from Hardy's repositories?

---

### Post by ShaunG on 2009-04-03
Nope, i had the same problem when using Hardys own repos so I thought maybe adding the repos on tors website might fix the problem.

---

### Post by ShaunG on 2009-04-03
Bump, would really like some help fixing this guys :)

---

### Post by ShaunG on 2009-04-04
Bump, please really need help fixing this.

---

### Post by ShaunG on 2009-04-06
Solved:

/dev/null and /dev/urandom and /dev/random had incorrect permission. Lord only knows how.

---

