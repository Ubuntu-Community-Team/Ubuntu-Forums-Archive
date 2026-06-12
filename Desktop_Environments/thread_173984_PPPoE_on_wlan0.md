---
title: "PPPoE on wlan0"
date: 2006-05-11
forum: Desktop Environments
---

### Post by Disabled on 2006-05-11
Yesterday night i've installed (with ndiswrapper) my dlink dwl-510 wireless lan card. All went ok, so i tried to configure, with pppoeconf, the connection with the ethernet modem attached to the AP. During the configuration all went straight, but when i type ```
sudo pon dsl-provider
``` this is the output ```
Plugin rp-pppoe.so loaded.
/usr/sbin/pppd: In file /etc/ppp/peers/dsl-provider: unrecognized option 'nic-wlan0'

```

So i tried to reconfigure the eth0 to connect to the modem, but then the error was the same only with eth0 instead of wlan0. Commenting the 'nic-eth0' line in dsl-provider file make pppoe work with eth0, but not with wlan0...

What can i do? 

Thank you all :)

---

### Post by Disabled on 2006-05-27
Ok, i resolved using this guide:

[http://www.ubuntuforums.org/showthread.php?t=183062&highlight=pppoeconf](http://www.ubuntuforums.org/showthread.php?t=183062&highlight=pppoeconf)

---

