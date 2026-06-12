---
title: "One Workstation - 3 TimeZones"
date: 2006-04-29
forum: Desktop Environments
---

### Post by NoLimitz on 2006-04-29
Can anyone tell me if it is possible to have different users on Ubuntu on different time zones with ease.

I work for 3 different companies via email in 3 different countries, and need a simple method of using one workstation in the different time zones.  My idea is 3 different users so that all my timestamps for work on those clients match the theirs.

Any tips would be really appreciated.

Thanks

Martin

---

### Post by Sendervictorius on 2006-04-30
Yes it is easy. 

The machine timezone (and default for users) is set by a symbolic link from /etc/localtime to a file in the /usr/share/zoneinfo directory that corresponds with what timezone you are in.

Individual users can be in different time zones. You need to set a TZ environment variable in each users login script file (.bashrc) in the users home directory.

A line like: 

TZ="Hongkong"; export TZ

should do the trick. The bit between the quotes corresponds to the file name appropriate found in the /usr/share/zoneinfo directory.

If you want to correspond with a multi-zone country, use the form:
TZ="US/Eastern"; export TZ

---

