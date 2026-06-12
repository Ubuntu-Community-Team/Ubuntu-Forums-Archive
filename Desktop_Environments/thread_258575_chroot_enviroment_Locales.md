---
title: "chroot enviroment: Locales"
date: 2006-09-16
forum: Desktop Environments
---

### Post by Anonii on 2006-09-16
Greetings, I set up my chroot enviroment today, to start practicing source to .deb building, and see the pros of sandboxing. Anyway...  Everytime I install something using apt-get I get this:
> (mychroot)root@habeeb:/home/habeeb# apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  build-essential
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
Need to get 6826B of archives.
After unpacking 49.2kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main build-essential 11.1 [6826B]
Fetched 6826B in 0s (13.2kB/s)
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_AU:en",
        LC_ALL = (unset),
        LANG = "en_AU.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
debconf: delaying package configuration, since apt-utils is not installed
Selecting previously deselected package build-essential.
(Reading database ... 9208 files and directories currently installed.)
Unpacking build-essential (from .../build-essential_11.1_i386.deb) ...
Setting up build-essential (11.1) ...


I followed this guide:
[https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot)
till the end. I did the locale steps too.

---

### Post by ayoli on 2006-09-16
once chrooted you may try 
```
dpkg-reconfigure locales
```

---

### Post by Anonii on 2006-09-16
Well, already done that afaik. But another question since you seem to know:
This guide: [https://wiki.ubuntu.com/HowToBuildDebianPackagesFromScratch](https://wiki.ubuntu.com/HowToBuildDebianPackagesFromScratch)
redirects to this guide: [https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot)
but then the starting guide says that after I have created the chroot enviroment I have to run pbuilder for a second time and it gives me this guide: [https://wiki.ubuntu.com/PbuilderHowto](https://wiki.ubuntu.com/PbuilderHowto)

Is this normal? Do I have to setup pbuilder twice? Once when I dont have a chroot enviroment and the second, when I have one? I'm kinda confused.

Thanks.

---

### Post by ayoli on 2006-09-16
i dunno really much about pbuilder, but according to your links you're supposed to run pbuilder under chrooted env.

---

### Post by Anonii on 2006-09-16
Ok, thanks. I messed up, and re-creating the chroot enviroment and I'll try the second pbuilder after this one.
Thanks again :]

(If anyone else, can help..)

---

### Post by Anonii on 2006-09-16
> **ayoli said:**
> i dunno really much about pbuilder, but according to your links you're supposed to run pbuilder under chrooted env.
> root@habeeb:/# dpkg-reconfigure locales
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_AU:en",
        LC_ALL = (unset),
        LANG = "en_AU.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Generating locales...
  en_GB.UTF-8... up-to-date
Generation complete.
Current default timezone: 'UTC'.
Local time is now:      Sat Sep 16 11:38:56 UTC 2006.
Universal Time is now:  Sat Sep 16 11:38:56 UTC 2006.
Run 'tzconfig' if you wish to change it.



Any ideas?

---

