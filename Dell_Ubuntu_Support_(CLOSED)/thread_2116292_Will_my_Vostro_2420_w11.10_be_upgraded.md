---
title: "Will my Vostro 2420 w/11.10 be upgraded?"
date: 2013-02-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by handrew on 2013-02-15
Feb 15th, 2013 Today Canonical announced... 
"The Ubuntu team is pleased to announce the release of Ubuntu 12.04.2 LTS....."

....Users of Ubuntu 10.04 and 11.10 will be offered an automatic upgrade to 12.04.2 via Update Manager....

Does this include the 11.10 that is deployed on Dell computers? I'd like to know if and when my Vostro 2420 will be upgraded to 12.04lts.

thanks

---

### Post by TheFu on 2013-02-15
You don't need to wait.

**Prep**
Being completely current with patches is very important.

```
$ sudo apt-get update
$ sudo apt-get dist-upgrade
```
Then make a complete backup. Sometimes things go badly and a backup will be worth it should that happen.

**Request the Upgrade**
```
$ sudo do-release-upgrade
```
will cause the update process.

---

