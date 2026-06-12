---
title: "Trying to get SMC6862W-G to work with ndiswrapper"
date: 2006-02-15
forum: Desktop Environments
---

### Post by Cyril on 2006-02-15
I have installed the windows driver with ndiswrapper and confirmed that it is installed with ndiswrapper -l.  And yes hardware is present.  But when I try to configure the interface using networking from my systems menu, the networking app just crashes.  

I believe the old drivers(the ones that come with ubuntu) are still being used instead of ndiswrapper because I used to get that same problem before I installed ndiswrapper.  How do I set things so that ndiswrapper will be used instead?

Or if anyone knows other methods of getting this wireless device to work please tell me.

---

### Post by Cyril on 2006-02-15
Anyone?  I believe this is a simple problem.

---

### Post by Cyril on 2006-02-17
Last bump

---

### Post by knitwit on 2006-02-17
I think you need to add the driver /etc/hotplug/blacklist to stop it loading on boot. You should find the name of the driver by going to System > Administration > Device Manager. Find the network adapter, click on the 'advanced' tab and you should find an entry called info.linux.driver

```

sudo gedit /etc/hotplug/blacklist
```

Just add the name of the Ubuntu driver module at the bottom, save then reboot.

I found [this]("http://ubuntuforums.org/showthread.php?t=22995") useful for sorting out my wifi woes!

---

