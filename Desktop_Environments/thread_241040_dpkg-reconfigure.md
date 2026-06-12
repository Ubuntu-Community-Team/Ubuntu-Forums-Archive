---
title: "dpkg-reconfigure"
date: 2006-08-21
forum: Desktop Environments
---

### Post by ronzo on 2006-08-21
Today I experienced the following problem:

```

/usr/bin$ sudo apt-get upgrade                                 Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  libkrb53
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/380kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
/bin/sh: /usr/sbin/dpkg-preconfigure: No such file or directory
(Reading database ...
dpkg: serious warning: files list file for package `debconf' missing, assuming package has no files currently installed.
dpkg: error processing /var/cache/apt/archives/libkrb53_1.4.3-5ubuntu0.1_i386.deb (--unpack):
 unable to open files list file for package `libpam0g': No such device or address
Errors were encountered while processing:
 /var/cache/apt/archives/libkrb53_1.4.3-5ubuntu0.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I found no solution for this and don't know what to try next.

Can anyone help?

---

### Post by smanos on 2006-08-31
I get a very similar bug - could anyone please help?

much appreciated

```

(Reading database ... dpkg: error processing /var/cache/apt/archives/libarts1c2a_1.5.2-0ubuntu1_i386.deb (--unpack):
 unable to open files list file for package `libmagick9': No such device or address
Errors were encountered while processing:
 /var/cache/apt/archives/libarts1c2a_1.5.2-0ubuntu1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by xyz on 2006-08-31
Tis one should help you guys out...at least for the most part:
[http://ubuntuforums.org/showthread.php?t=186672](http://ubuntuforums.org/showthread.php?t=186672)

---

