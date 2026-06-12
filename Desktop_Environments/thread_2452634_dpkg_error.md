---
title: "dpkg error"
date: 2020-10-26
forum: Desktop Environments
---

### Post by ewm on 2020-10-26
Good Day,
I have just upgraded to Ubuntu 20.04 and installed mmex 1.3.5 using downloaded deb package.
I am now getting this error when running sudo apt upgrade. I have tried all the normal recommended fixes - any suggestions on how to fix this would be most welcome.
Thanks
*sudo apt upgrade*

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 mmex : Depends: wx3.0-i18n but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

*sudo apt 'apt --fix-broken install*

dpkg: error processing archive /var/cache/apt/archives/wx3.0-i18n_3.0.4+dfsg-15b
uild1_all.deb (--unpack):
 trying to overwrite '/usr/share/locale/ca/LC_MESSAGES/wxstd.mo', which is also 
in package wx3.1-i18n 3.1.3-1.focal
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/wx3.0-i18n_3.0.4+dfsg-15build1_all.deb

---

### Post by ActionParsnip on 2020-10-26
What is the output of:
```

lsb_release -a; uname -a; apt-cache policy mmex wx3.0-i18n

```

My PPA sense is tingling. The package system doesn't like overlapping files like that. You can force install the deb file but it doesn't solve the issue

---

### Post by ewm on 2020-10-26
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 20.04.1 LTS
Release:	20.04
Codename:	focal
Linux eric-G31M-ES2C 5.4.0-52-generic #57-Ubuntu SMP Thu Oct 15 10:57:00 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
mmex:
  Installed: 1.3.5-1~tessa
  Candidate: 1.3.5-1~tessa
  Version table:
 *** 1.3.5-1~tessa 100
        100 /var/lib/dpkg/status
wx3.0-i18n:
  Installed: (none)
  Candidate: 3.0.4+dfsg-15build1
  Version table:
     3.0.4+dfsg-15build1 500
        500 [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) focal/universe amd64 Packages
        500 [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) focal/universe i386 Packages

---

### Post by ewm on 2020-10-27
Hi,
Wasted too much time on this problem. I cleaned out apt/cache and checked the sources lists for any obvious errors but no success so purged mmex and then installed wx3.0-i18n- everything ok : Will try re installing mmex.deb  when I have time meanwhile I am using the snap version which is painfully slow.
Thanks for your time.

---

