---
title: "[CentOS] no --log-file option in rsync (2.6.8)"
date: 2008-06-17
forum: Fedora/RedHat and derivatives
---

### Post by altonbr on 2008-06-17
I've created a fantastic script for headless rsyncing between two servers over SSH. The problem is, I created the script for and under Ubuntu/Debian.

When I had to use this script on a CentOS server I was surprised to see that the option '--log-file' does not exist!

> rsync: --log-file=/root/logs/rsync-20080617-1213751819.log: unknown option
rsync error: syntax or usage error (code 1) at main.c(1231) [client=2.6.8]


This CentOS 5.1 server has rsync 2.6.8 while Ubuntu 8.04 uses 2.6.9. I've been using rsync since before 2.6.8, so why is there this difference between the two distros and what can I do about it?

---

### Post by dca on 2008-06-18
Does it have something to do w/ Ubuntu having root disabled by default (sudo)???  You show the log files going to /root...  I dunno'...
 
...then again, here:  [http://www.ss64.com/bash/rsync_options.html](http://www.ss64.com/bash/rsync_options.html)
 
I don't see --log file listed as an avail option, only'--log-format=FORMAT'...  Check the rsync.conf file and see if anything is in there referencing default log locations...

---

