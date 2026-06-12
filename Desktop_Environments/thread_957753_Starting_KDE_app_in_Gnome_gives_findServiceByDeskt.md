---
title: "Starting KDE app in Gnome gives findServiceByDesktopPath: error"
date: 2008-10-24
forum: Desktop Environments
---

### Post by billstei on 2008-10-24
After installing a development version of a particular KDE app I was getting an error like this (could be one of many KDE apps) when trying to start it from Gnome:
 
findServiceByDesktopPath: [whatever-app-you-are-running].desktop not found

and it was hard to find any info on it, so I thought I would mention here what fixed it.  I simply ran (as a normal user, not sudo):

kbuildsycoca4

Hope this helps someone out there.

Bill

---

### Post by jscordia on 2009-11-22
Thanks a lot!!

I was struggling with two problems:
* the knode configuration dialog ("configure dialog" from knode menu) was empty, and returned when launched from a terminal:

findServiceByDesktopPath: knode_config_accounts.desktop not found
findServiceByDesktopPath: knode_config_appearance.desktop not found
findServiceByDesktopPath: knode_config_read_news.desktop not found
findServiceByDesktopPath: knode_config_post_news.desktop not found
findServiceByDesktopPath: knode_config_privacy.desktop not found
findServiceByDesktopPath: knode_config_cleanup.desktop not found

* Kontact did not provide access to knode, although it was installed. When run from a terminal, I obtained:

Calling appendChild() on a null node does nothing.

By simply running kbuildsycoca4, the two problems have been solved!!

Thanks!! :KS:o

Julien

---

