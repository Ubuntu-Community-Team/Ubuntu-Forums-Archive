---
title: "apt wants to re-upgrade already upgraded packages"
date: 2006-08-06
forum: Desktop Environments
---

### Post by fallingleaf on 2006-08-06
I'm running Dapper installed from live cd.  first I used Synaptic to try to upgrade everything. Because I have a slow connection I did this over several days, clicking "mark all upgrades", "apply", then "cancel" and let it install what it had downloaded  so far.  Finally it was almost finished but there were two packages it couldn't get.  I thought I might have better luck if I used the repositories for my country (Costa Rica), so so I opened up /etc/apt/sources.list and replaced every "archives.ubuntu.com" with "cr.archives.ubuntu.com".  

$ apt-get update

So far so good, then

$apt-get upgrade

"88 packages need to be upgraded.  need to get 69.6MB of archives"

some of the upgrades I know were already upgraded, for example linux-image-2.6.15.26.386!  I am well aware of that upgrade because it messed up my grub menu.lst.

Also all these things it's trying to download are already in /var/cache/apt

How can I get apt to realize the packages are already upgraded?

Edit: I tried changing sources.list back to the way it was, but it didn't help.

Thanks,
fallingleaf

---

