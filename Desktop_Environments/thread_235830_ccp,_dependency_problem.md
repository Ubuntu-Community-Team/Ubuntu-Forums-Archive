---
title: "ccp, dependency problem?"
date: 2006-08-13
forum: Desktop Environments
---

### Post by boca raton on 2006-08-13
Using Ubuntu 5.10.  Synaptic indicates ccp and cpp-4.0 can be upgraded.  When I attempt to upgrade I get the following messages;

cpp:
  Depends: cpp-4.0 (>=4.0.3) but 4.0.1-4ubuntu9 is to be installed

cpp-4.0:
  Depends: gcc-4.0-base (=4.0.3-1ubuntu5) but 4.0.1-4ubuntu9 is to be installed

Any suggestions to fixing this?

thanks

---

### Post by jchau on 2006-08-13
Seems like you can't get all the packages necessary to perform the update.  Try updating your package information by pressing Ctrl+R in Synaptic.  Also enable the security update and backports repositories.  

Also, the packages website for Ubuntu indicates that those versions aren't available for Breezy, so I don't quite know why you are getting the option to update.  

If you really want to update, and you can't fix it in Breezy, you can try getting the dependencies from Dapper repositories and install those (but it's risky because they probably haven't been tested on Breezy).  Another option that is more likely to work will be to update to Dapper (Dapper often gets new packages that Breezy doesn't).

---

### Post by boca raton on 2006-08-13
My overall goal is to upgrade to Dapper, I have it on another machine and it is great!.  

But in following 'DapperUpgrades.html' I should;

"Confirm that you have version "0.42.2ubuntu12~breezy1" or newer of Update-manager installed"

I have not been able to change the Update-manager, and I suspect it is because cpp & cpp-4.0 won't upgrade.

So, I'm trying to solve cpp & cpp-4.0 first.

---

