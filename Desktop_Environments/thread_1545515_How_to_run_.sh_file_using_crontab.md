---
title: "How to run .sh file using crontab?"
date: 2010-08-04
forum: Desktop Environments
---

### Post by vksingh on 2010-08-04
Hi,

I have a .sh file which i want to run using crontab at a specific time with root privilege.

I put an entry in root's crontab as the following:

sh /home/vivek/ifconfig/college.sh

But, the file do not get executed at a given time.


Please help.

Thanks,

Vivek

---

### Post by anglican on 2010-08-04
> **vksingh said:**
> Hi,

I have a .sh file which i want to run using crontab at a specific time with root privilege.

I put an entry in root's crontab as the following:

sh /home/vivek/ifconfig/college.sh

But, the file do not get executed at a given time.


Please help.

Thanks,

VivekDid you also include the necessary time fields:
```
              field                      allowed values
              -----                      --------------
              minute                     0-59
              hour                       0-23
              day of month               1-31
              month                      1-12 (or names, see below)
              day of week                0-7 (0 or 7 is Sun, or use names)

       A field may be an asterisk (*), which always stands for ``first-last''.

```e.g.
```
0 1 * * * sh /home/vivek/ifconfig/college.sh
```which means "run this command at 1:00 am on every day in every month".

H

---

