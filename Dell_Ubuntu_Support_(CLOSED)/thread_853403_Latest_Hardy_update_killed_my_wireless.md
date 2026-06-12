---
title: "Latest Hardy update killed my wireless"
date: 2008-07-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Franc88 on 2008-07-08
I have a Dell 1525 that I had a working wireless adapter, a Broadcom BCM4310, for version 8.04.  Now with the latest update, the wireless adapter is not working.  

Under Hardware Drivers, it shows it is Enabled but under Status, it says "Not In Use".  I know this driver is proprietary but was wondering if anyone knows how to resolve this issue.

I've already tried to re-install the driver and even boot from an earlier version of Hardy but no luck.  

If there is no work around, can someone tell me how to roll back the update and remove it from the system so I can use the  "older" 8.04 version.

Thanks.

---

### Post by Franc88 on 2008-07-09
Sorry but this is a duplicate thread and I can't delete it.

---

### Post by friendofpugs on 2008-07-09
This exact problem is happening to me too. Any advice would be much appreciated. Thanks! :confused:

---

### Post by Franc88 on 2008-07-09
> **friendofpugs said:**
> This exact problem is happening to me too. Any advice would be much appreciated. Thanks! :confused:

Hi Pugs,

Please check this other thread for a solution:  [http://ubuntuforums.org/showthread.php?t=853410](http://ubuntuforums.org/showthread.php?t=853410)

If you follow the link and the steps, you should be able to correct the issue regarding your wireless.  If you have any other questions, you can post it on that thread or PM me and I'll try my best to help.  Having no wireless on a laptop sort of defeats the purpose of having one.

---

### Post by superm1 on 2008-07-10
> **Franc88 said:**
> Hi Pugs,

Please check this other thread for a solution:  [http://ubuntuforums.org/showthread.php?t=853410](http://ubuntuforums.org/showthread.php?t=853410)

If you follow the link and the steps, you should be able to correct the issue regarding your wireless.  If you have any other questions, you can post it on that thread or PM me and I'll try my best to help.  Having no wireless on a laptop sort of defeats the purpose of having one.
If you are encountering this issue, please activate hardy-proposed to test the fix there.  It should resolve it.  You can leave a comment on this bug after it works for you:
[https://bugs.edge.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/243930](https://bugs.edge.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/243930)

---

