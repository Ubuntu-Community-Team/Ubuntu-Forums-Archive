---
title: "A copy of the C library was found in an unexpected directory:   '/lib/i386-linux-gnu/"
date: 2012-03-12
forum: Desktop Environments
---

### Post by bijune on 2012-03-12
Hi, all

I am using ubuntu 11.10. Last time I tried running update, it failed. After that an warning icon appeared in the place of update notification. I follow the help message, try the following command

```
sudo apt-get -f install
```and get the following 

```
The following extra packages will be installed:
  libc6
Suggested packages:
  glibc-doc
The following packages will be upgraded:
  libc6
1 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
1 not fully installed or removed.
Need to get 0 B/3,800 kB of archives.
After this operation, 8,192 B of additional disk space will be used.
Do you want to continue [Y/n]?
```After press Y, firstly I get some dpkg warnings, such as 

```
dpkg: warning: files list file for package `libgwibber-gtk2' missing, assuming package has no files currently installed.
```after those warnings are

```
A copy of the C library was found in an unexpected directory:
  '/lib/i386-linux-gnu/libc-2.13.so'
It is not safe to upgrade the C library in this situation;
please remove that copy of the C library or get it out of
'/lib/i386-linux-gnu' and try again.

dpkg: error processing /var/cache/apt/archives/libc6_2.13-20ubuntu5.1_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.13-20ubuntu5.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```The problem really borders me. Can you help me?
Thanks

best,
June

---

### Post by bijune on 2012-03-13
Anyone help?

---

### Post by suside on 2012-03-27
I didn't have ```
dpkg: warning: files list file for package...
```
but only
```
A copy of the C library was found in an unexpected directory:
```
so heres what i did
[LIST=1]
[*]Copy /lib/i386-linux-gnu/libc-2.13.so to /lib/delme
[*]Copy every file from /lib/i386-linux-gnu/ that apt-get complain about to /lib/delme
[*]Edit /etc/ld.so.conf.d/libc.conf and add there "/lib/delme"
[*]Run sudo ldconfig -v
[*](This step is danger, I have a running "sudo mc" in case something goes wrong) Now you can safely delete files from /lib/i386-linux-gnu/ you just copied
[*]Run "sudo apt-get -f install" and it should work now
[*]Finally remove entry from /etc/ld.so.conf.d/libc.conf and delete /lib/delme
[/LIST]

---

