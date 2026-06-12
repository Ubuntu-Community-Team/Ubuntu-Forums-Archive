---
title: "Apache segmentation faults"
date: 2009-10-26
forum: Desktop Environments
---

### Post by lduperval on 2009-10-26
Hi,

I am trying to get PHP5, MySQL and Apache to work, but I keep seing this error in my log files:

```
[Mon Oct 26 23:35:57 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Mon Oct 26 23:35:57 2009] [info] Server built: Aug 18 2009 14:27:36
[Mon Oct 26 23:36:03 2009] [notice] child pid 23860 exit signal Segmentation fault (11)
[Mon Oct 26 23:44:16 2009] [notice] child pid 23861 exit signal Segmentation fault (11)
[Mon Oct 26 23:44:16 2009] [notice] child pid 23862 exit signal Segmentation fault (11)

```

This happens when I try to load a PHP page. Ging to the directory says "It works".

Any ideas?

L

---

### Post by CyberJack on 2009-10-27
Do you get any output when requesting a php page?
Maybe one of these will help:

[http://ubuntuforums.org/showthread.php?t=197020](http://ubuntuforums.org/showthread.php?t=197020)
[https://bugs.launchpad.net/ubuntu/+source/php5/+bug/392521](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/392521)

---

### Post by lduperval on 2009-10-27
Yes, I do. I created a php test page with this in it:

<?php phpinfo() ?>

and I see the PHP info. So it's not a PHP issue, but maybe a PHP/mysql problem. And according to the bug reports, looks like the latter. OK, I have to figure out how to fix this.

L

---

