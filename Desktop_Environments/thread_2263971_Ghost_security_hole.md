---
title: "Ghost security hole"
date: 2015-02-04
forum: Desktop Environments
---

### Post by williepabon on 2015-02-04
[COLOR=#333333][FONT=Ubuntu]Hi:
I recently read an article referring to the subject that affects systems running glibc-2.2 or earlier. The news said that Canonical patched all LTS releases back to 10.04. I checked my Ubuntu 12.04 LTS machine (32bit) by running in terminal(as instructed in the article):[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]williepabon@williepabon-VGN-N130G:~$ dpkg -l libc6
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name Version Description
+++-==============-==============-============================================
ii libc6 2.15-0ubuntu10 Embedded GNU C Library: Shared libraries
williepabon@williepabon-VGN-N130G:~$[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Does this mean that the library in my machine is not patched yet? So, I ran a s/w update on my machine,[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]sudo apt-get update
sudo apt-get upgrade[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]After that, I rebooted and ran dpkg -l libc6 again, but got the same previous results. Please, advice. Thanks[/FONT][/COLOR]

---

### Post by Habitual on 2015-02-04
from [https://www.digitalocean.com/community/tutorials/how-to-protect-your-linux-server-against-the-ghost-vulnerability](https://www.digitalocean.com/community/tutorials/how-to-protect-your-linux-server-against-the-ghost-vulnerability) for output value of 
```
ldd --version
```

for "Ubuntu & Debian" section.

---

### Post by mcduck on 2015-02-04
It's patched. The last part of the version number tells the Ubuntu patch applied to the file, so you don't have *libc6 2.15-0*, but instead *libc6 2.150**ubuntu10***. You can see the changelog for the versions (with the CVE numbers you can compare to the actual security warnings) here: [http://changelogs.ubuntu.com/changelogs/pool/main/e/eglibc/eglibc_2.15-0ubuntu10.10/changelog]("http://changelogs.ubuntu.com/changelogs/pool/main/e/eglibc/eglibc_2.15-0ubuntu10.10/changelog")

(patching doesn't mean updating to latest version, but instead applying the security fixes to whatever version is in use, so in this casethe problem wasn't fixed by updatnig you to later than 2.2 but instead fixing the issue in the 2.15 version)

---

### Post by bashiergui on 2015-02-04
Also this link has a script you can run to test if you're vulnerable.
[http://www.cyberciti.biz/faq/cve-2015-0235-patch-ghost-on-debian-ubuntu-fedora-centos-rhel-linux/](http://www.cyberciti.biz/faq/cve-2015-0235-patch-ghost-on-debian-ubuntu-fedora-centos-rhel-linux/)

---

### Post by williepabon on 2015-02-04
Habitual:
Thanks for answering. Another guy at Canonical gave me the answer by pointing me to the specific bug. And running your command verified that my machine was updated.

williepabon@williepabon-VGN-N130G:~$ ldd --version
ldd (Ubuntu EGLIBC 2.15-0ubuntu10.10) 2.15
Copyright (C) 2012 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
Written by Roland McGrath and Ulrich Drepper.

wp

---

### Post by deadflowr on 2015-02-04
[COLOR=#333333][FONT=Ubuntu]> The news said that Canonical patched all LTS releases back to 10.04.[/FONT][/COLOR]

Only 10.04 and 12.04 needed the patch.
Versions released after (summer?)2013 have a fix already in place  --built in.
So 14.04LTS and 14.10 don't need a patch.
(The fix was marked as a minor bug fix at the time, so it wasn't pushed to existing versions)

Everything between 10.04 and 12.04 is dead, same for everything between 12.04 and 14.04.
So no need to patch a dead release.

---

### Post by Habitual on 2015-02-05
> **williepabon said:**
> Habitual:
Thanks for answering. Another guy at Canonical gave me the answer by pointing me to the specific bug. And running your command verified that my machine was updated.

williepabon@williepabon-VGN-N130G:~$ ldd --version
ldd (Ubuntu EGLIBC 2.15-0ubuntu10.10) 2.15
Copyright (C) 2012 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
Written by Roland McGrath and Ulrich Drepper.

wp


Glad it all worked out!

---

### Post by mc4man on 2015-02-05
I'm gathering you, (or what you read),  really didn't mean glibc-2.2 as Ubuntu likely never used that early a version ever..

---

### Post by williepabon on 2015-02-06
> **mc4man said:**
> I'm gathering you, (or what you read),  really didn't mean glibc-2.2 as Ubuntu likely never used that early a version ever..

Got the info from this article:

[http://www.techrepublic.com/article/the-ghost-security-hole-perfectly-illustrates-the-efficiency-of-open-source/?tag=nl.e101&s_cid=e101&ttag=e101&ftag=TRE684d531](http://www.techrepublic.com/article/the-ghost-security-hole-perfectly-illustrates-the-efficiency-of-open-source/?tag=nl.e101&s_cid=e101&ttag=e101&ftag=TRE684d531)

---

### Post by mc4man on 2015-02-06
> **williepabon said:**
> Got the info from this article:

[http://www.techrepublic.com/article/the-ghost-security-hole-perfectly-illustrates-the-efficiency-of-open-source/?tag=nl.e101&s_cid=e101&ttag=e101&ftag=TRE684d531](http://www.techrepublic.com/article/the-ghost-security-hole-perfectly-illustrates-the-efficiency-of-open-source/?tag=nl.e101&s_cid=e101&ttag=e101&ftag=TRE684d531)

He didn't term that correctly at all - vulnerability was *introduced* in glibc-2.2, more accurate would be  - 
> The first vulnerable version of the GNU C Library affected by this is glibc-2.2, released on November 10, 2000. We identified a number of factors that mitigate the impact of this bug. In particular, we discovered that it was fixed on May 21, 2013 (between the releases of glibc-2.17 and glibc-2.18). Unfortunately, it was not recognized as a security threat; as a result, most stable and long-term-support distributions were left exposed including Debian 7 (wheezy), Red Hat Enterprise Linux 6 & 7, CentOS 6 & 7, Ubuntu 12.04, for example.



---

### Post by williepabon on 2015-02-06
**mc4man:**

Thanks for the info and education. Probably, somebody from the Ubuntu technical side should enlighten Jack Wallen (the writer of the article).

wp

---

### Post by mc4man on 2015-02-06
Side note:
One  thing that used to mess with me was glancing at versions & thinking that for instance, 2.2 was higher than 2.15 which it's obviously not, though 2.2 is higher than 2.1.5

---

