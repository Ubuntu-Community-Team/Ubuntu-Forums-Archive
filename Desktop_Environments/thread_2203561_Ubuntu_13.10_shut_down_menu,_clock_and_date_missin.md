---
title: "Ubuntu 13.10: shut down menu, clock and date missing"
date: 2014-02-04
forum: Desktop Environments
---

### Post by theredbaron908 on 2014-02-04
I have gnome fallback session. It was fine, and then one day I noticed that those items were missing from the top bar. I tried updating and upgrading, but it fixed nothing. When I try
sudo killall unity-panel-service
unity-panel-service: no process found


but also
sudo apt-get install unity
Reading package lists... Done
Building dependency tree       
Reading state information... Done
unity is already the newest version.
The following package was automatically installed and is no longer required:
  openjdk-7-jre-lib
Use 'apt-get autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



I tried a few attempts posted online, but nothing helped.

---

### Post by Erik1984 on 2014-02-04
I've seen the clock disappear from the panel in Unity but after a reboot it was back. Sorry if I missed it in your post but are those elements still gone from the panel after a reboot?

---

### Post by theredbaron908 on 2014-02-04
Yes, definitely rebooting does NOT help.. Clock, date and shutdown menu are constantly and consistently missing.

---

### Post by dagolfnut on 2014-02-20
I am having the same issue as the OP. The top menu bar works if I log in with Unity, which I don't like, but not with the Gnome Fallback. Anyone have any advise on how to fix this?

---

### Post by soum_axetuirk on 2014-02-20
It probably uninstalled.
try this in terminal 
```

sudo apt-get install indicator-datetime

```

---

### Post by dagolfnut on 2014-02-20
Okay, tried that and it read that I have the latest version installed.

---

### Post by leftyleo on 2014-03-13
i use :

killall unity-panel-service

---

