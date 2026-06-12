---
title: "PM: resume from disk failed.  PM libcrypt version 1.4.5 loading image data 100%"
date: 2011-03-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by leonbravo on 2011-03-17
Hi, 

My DELL XPS M1330 is unavailable to hibernate. I upgrade to ubuntu 10.10 from 10.04 recently, before I solved the problem installing the uswsusp [URL="http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/"].  The kernel is 2.6.35-27-generic. 

I compiled some information from the startup:  libcrypt version 1.4.5 / loading image data .. total image i/o is 26.7 Mb 100% done

after which the system freeze. After ctrl+Alt+Del the system starts as after a shutdown (no charging previous session). So I checked the log at /var/log/kern.log:   PM: Resume from disk failed.
Mar 17 17:29:46 leon kernel: [    0.732251] registered taskstats version 1
Mar 17 17:29:46 leon kernel: [    0.732782]   Magic number: 3:519:502


I followed many different threats and bug reports ( http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/[/URL], [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/692269?comments=all]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/692269?comments=all"), [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/522998]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/522998")).  

I couldn't find a solution for this. Any help is rather appreciated.

---

