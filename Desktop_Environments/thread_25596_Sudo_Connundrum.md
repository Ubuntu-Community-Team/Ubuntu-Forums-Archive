---
title: "Sudo Connundrum"
date: 2005-04-10
forum: Desktop Environments
---

### Post by Mr_THX on 2005-04-10
When I log onto the computer it tells me that I need to add my computer name to the hosts file.  In order to do that I need to have permission to write to the hosts file.  But when I type in sudo or I try to switch to root I get the following error:

sudo: unable to lookup debian via gethostbyname ()

I know that I need to edit my hosts file with sudo or root to fix this problem but the problem is preventing me from getting to either of them.  When su prompts me for my password it doesnt work with my userpassword either.

---

### Post by crim on 2005-04-10
Just boot into rescue mode or with any live cd, mount your hard drive and edit the hosts file. Then reboot and all should be good.

---

