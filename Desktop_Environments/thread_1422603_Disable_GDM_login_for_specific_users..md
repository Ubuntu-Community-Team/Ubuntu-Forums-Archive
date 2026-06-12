---
title: "Disable GDM login for specific users."
date: 2010-03-05
forum: Desktop Environments
---

### Post by thndrchld on 2010-03-05
Hello.  I have two computers here at my office that run Ubuntu.  One runs 9.10, and the other runs 8.04.

Both are used to archive data for our customers.  We have some custom scripts I wrote that manage users, customer accounts, data archival and retrieval, etc.  My problem is that my employees have recently discovered that they can log into the graphical side, and have been circumventing the scripts, causing problems with accounting.

Is there a way to disable GDM login for specific users, without affecting their text console logins?  I don't want to disable the gui entirely, because the admins (myself included) need to be able to access it freely.

The scripts run as the user login script from passwd, and terminate the console session when finished.  

I don't particularly care if the user gains access to a console prompt.  The permissions are appropriately locked down, and most of my users aren't savvy enough to cause a problem anyway.  The gui login is my problem.

Any help would be appreciated.  I can provide more info if you need it.

Thanks.

---

