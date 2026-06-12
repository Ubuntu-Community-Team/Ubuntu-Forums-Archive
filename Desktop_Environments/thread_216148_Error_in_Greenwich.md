---
title: "Error in Greenwich"
date: 2006-07-15
forum: Desktop Environments
---

### Post by waffen on 2006-07-15
When I try to run this program I receipt this error:

mario@laptop2:~$ greenwich
Can't locate Gtk2/GladeXML.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/bin/greenwich line 23.
BEGIN failed--compilation aborted at /usr/bin/greenwich line 23.

Any idea??

---

### Post by Sendervictorius on 2006-07-16
You have not got the Gtk2::GladeXML perl module installed on your computer.

There is a bug in  Bugs in greenwich in ubuntu. Check out this link:
[https://launchpad.net/distros/ubuntu/+source/greenwich/+bugs](https://launchpad.net/distros/ubuntu/+source/greenwich/+bugs)

---

### Post by waffen on 2006-07-30
Yes, Its correct! Thanks!:D

---

