---
title: "/etc/apt/apt.conf.d"
date: 2008-12-26
forum: General Help
---

### Post by b0bk3ll3yjr on 2008-12-26
Hello- I recently configured my first Ubuntu 7.10 server and performed the steps in the following link to configure security updates to happen automatically.  I am looking for additional information explaining when this script will run and what the syntax of the file names in the /etc/apt/apt.conf.d mean. For example, 50unattended-upgrades.  Obviously, putting the file in this location allows is to run at some point in time but when. 

[https://help.ubuntu.com/community/AutomaticSecurityUpdates](https://help.ubuntu.com/community/AutomaticSecurityUpdates)

Thanks.:P

---

### Post by dcstar on 2008-12-27
> **b0bk3ll3yjr said:**
> Hello- I recently configured my first Ubuntu 7.10 server and performed the steps in the following link to configure security updates to happen automatically.  I am looking for additional information explaining when this script will run and what the syntax of the file names in the /etc/apt/apt.conf.d mean. For example, 50unattended-upgrades.  Obviously, putting the file in this location allows is to run at some point in time but when. 

[https://help.ubuntu.com/community/AutomaticSecurityUpdates](https://help.ubuntu.com/community/AutomaticSecurityUpdates)


All jobs in cron.weekly are run weekly, all jobs in cron.daily are run daily etc etc.

If you want to know more look up the cron man pages.

---

### Post by gTinker on 2008-12-27
[QUOTE=b0bk3ll3yjr]Hello- I recently configured my first Ubuntu 7.10 server and performed the steps in the following link to configure security updates to happen automatically.  I am looking for additional information explaining when this script will run and what the syntax of the file names in the /etc/apt/apt.conf.d mean. For example, 50unattended-upgrades.  Obviously, putting the file in this location allows is to run at some point in time but when. 
[/QUOTE]

The files in there are parsed (read) by the package manager when it is doing some package management for you. 

The prepended numbers refer to (and determine) the order in which the (configuration) files are read.

---

