---
title: "KPilot / Palm Zire 72 / Several Users"
date: 2005-05-15
forum: Desktop Environments
---

### Post by OCon on 2005-05-15
Hi

I cannot find a solution for my problem getting kpilot to work for all my users

Via modprobe I inserted the vendor and product id as explained on the kpilot webpage
I started kpilot under my user let him detect automatically if he finds a handheld which he did and synced.

Then I switched to my wife's user account and wanted to sync her Palm too. But I cannot get it to work. It always tells me that it cannot find a device

Any tips?

Thanks
Marc

---

### Post by praekon on 2005-05-26
Hi,
do you want to share one Palm?
The Access restrictions for Palm Devices depends on the DEV entry (eg /dev/pilot)

Under Ubuntu your Standart User Account is in the admin group.
When /dev/pilot is running under UDev with mode '660' other's than you
and root will not have access. You need '666' for than.
The short Tip for Palm devices i wrote in this forum should work for every user.
I can access to my palm also on Fedora, and there i am a 'normal' user, and not in the admin group.

greets
praekon

---

