---
title: "Upgrade from  2.6.20 to Ubuntu 7.04"
date: 2009-03-13
forum: General Help
---

### Post by big136 on 2009-03-13
Hi,
how to Upgrade from  2.6.20 to Ubuntu 7.04 ?

Thank you.

---

### Post by madverb on 2009-03-13
Umm... I guess the only way to find out is to try do an upgrade. If that fails you may need to get old copies and upgrade through the versions.

---

### Post by heindsight on 2009-03-13
2.6.20 sounds like a Linux kernel version number, not an Ubuntu release number. Which Ubuntu release are you using? You can find this out by opening a terminal and running the command:
```
lsb_release -a
```

You should keep in mind that Ubuntu 7.04 (Fiesty) is obsolete. You'd be better off upgrading to either Ubuntu 8.04 LTS (the long term support release), or Ubuntu 8.10 (the newest stable release).

If you have kernel 2.6.20, chances are you already have Ubuntu 7.04 (I don't remember exactly but I believe that was the kernel version used in Fiesty). With such an old version, your best option for upgrading is probably to back up your data, downloading a CD image for either Ubuntu 8.04 or 8.10 and doing a fresh install.

Have a look at this page for more information on upgrading: [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by big136 on 2009-03-16
thank you here is the result :
 lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.04
Release:        7.04
Codename:       feisty
 then I'm already in 7.04 ?

---

### Post by heindsight on 2009-03-16
> **big136 said:**
> thank you here is the result :
 lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.04
Release:        7.04
Codename:       feisty
 then I'm already in 7.04 ?

Indeed, you are already running 7.04
As I said before, I'd recommend you upgrade to at least 8.04

---

### Post by jespdj on 2009-03-16
You're indeed confused about the version numbers. 2.6.20 and 7.04 are the version numbers of two different things, so "upgrading from 2.6.20 to 7.04" makes no sense in this case.

2.6.20 is the version of the Linux kernel that is included with Ubuntu 7.04.

Note that Ubuntu 7.04 is already an old version (from April 2007) - the current version of Ubuntu is 8.10 (October 2008).

---

### Post by geirha on 2009-03-16
Since 7.04 is no longer supported, you should at least upgrade to Ubuntu 7.10 Gutsy Gibbon [https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)

Gutsy is supported until this april (2009), so I recommend you further upgrade to Ubuntu 8.04 LTS Hardy Heron [https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades)

Hardy is a long term support release, so it is supported for another two years (until april 2011).

EDIT: err. heindsight already covered this. Sorry

---

