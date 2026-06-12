---
title: "Can't remove package, no errors"
date: 2006-04-18
forum: Desktop Environments
---

### Post by steve0921 on 2006-04-18
I can't remove the package gstreamer0.8-jack from my system. There is no error message, the process just hangs while removing:

```
steve@nargothrond:~$ sudo dpkg --purge gstreamer0.8-jack --force-all
(Reading database ... 109694 files and directories currently installed.)
Removing gstreamer0.8-jack ...

```

At this point I can do nothing but close the terminal (after waiting over half an hour). I can't even send an interrupt. The very same thing has also happened during configuration when I tried to reinstall the package. As such, it is currently half configured.

I need to get this sorted out to upgrade to dapper (otherwise, the same thing happens during dist-upgrade, except with much worse results). Is there anything I can do?

Update: Rebooting into repair mode and using only command line environement I was able to remove it. I don't know why.

-Steve

---

### Post by apjone on 2006-04-19
if something dosent work with sudo , try 'su -' to root. Now and again sudo wont work with certain commands , and dosent show some commands. eg sudo on redhat will not show ifup / ifdown

---

