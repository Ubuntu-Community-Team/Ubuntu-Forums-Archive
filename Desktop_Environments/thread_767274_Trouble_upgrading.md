---
title: "Trouble upgrading"
date: 2008-04-25
forum: Desktop Environments
---

### Post by Zurdan on 2008-04-25
In the past I have installed moblock but for the past few months now I have been getting an error message when trying to update it.  The update in question is moblock-nfq (from version 0.8-32+feisty to 0.8-40+feisty)  So have had to endure an error message every time I run the update manager, big deal.  
But now I have been unable to upgrade to 8.04.  Every time I click on the upgrade the manager seems to freeze and I have to force quit it.  Any suggestions on how to fix this?  Thanks.

Edit:
by the way the error message I get is:
E: /var/cache/apt/archives/moblock-nfq_0.8-40+feisty_i386.deb: subprocess new pre-removal script returned error exit status 6

---

### Post by jre on 2008-04-30
> **Zurdan said:**
> Edit:
by the way the error message I get is:
E: /var/cache/apt/archives/moblock-nfq_0.8-40+feisty_i386.deb: subprocess new pre-removal script returned error exit status 6

Have a look at /var/log/moblock-control.log to see what is causing this error.
If you deleted a file you can download it from the development repository ([http://moblock-deb.svn.sourceforge.net/viewvc/moblock-deb/moblock/moblock-0.8/moblock-0.8/debian/](http://moblock-deb.svn.sourceforge.net/viewvc/moblock-deb/moblock/moblock-0.8/moblock-0.8/debian/))
If I remember correctly there were various issues with outdated conf files (lacking necessary variables). This might be fixed by downloading the actual moblock.conf to /etc/moblock/moblock.conf

---

