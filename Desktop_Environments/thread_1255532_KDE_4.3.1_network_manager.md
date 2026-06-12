---
title: "KDE 4.3.1 network manager"
date: 2009-09-01
forum: Desktop Environments
---

### Post by jimbo99 on 2009-09-01
Apparently after upgrading to kde 4.3.1 the network manager keeps crashing.  Anyone have the same experience or know why?

---

### Post by jimbo99 on 2009-09-01
I found on further investigation that the cause of the crash is centered around the wireless element of the network manager.  If wireless is enabled it will crash.  If it is not, it will not.  Prior to this upgrade this didn't happen.

---

### Post by jimbo99 on 2009-09-01
I upgraded a second computer, a notebook, that relies on wireless and was disappointed to find the same issue.  This meant that I couldn't use the notebook as a wireless device until I worked out the issues.  I decided to disable wireless in the knetworkmanager and then turned it back on.  I was then prompted for my password by kwallet.   After that it connected me and the knetworkmanager no longer crashes.  But, I don't know how long term a solution that will be, it might happen again the next time I reboot.

---

### Post by volchara on 2009-09-01
Bump!

Same thing happens to me. 

System:

Thinkpad T60, 
03:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)

KDE 4.3.1

---

### Post by jimbo99 on 2009-09-01
Did you try what I tried?  Right click on the knetworkmanager icon in the system tray and choose to uncheck the enable wireless.  Then click to enable it.  After being prompted you should be able to use wireless and the crash should go away.  For how long (such as till the next reboot) I couldn't tell you.

---

### Post by sirwitti on 2009-09-02
same here: it seems to crash every 30 seconds or so.
and after disabling and reenabling it seems to work.

can anyone else confirm that it works after doing this?


btw i already filed a bug report:

[https://bugs.kde.org/show_bug.cgi?id=205962](https://bugs.kde.org/show_bug.cgi?id=205962)

---

### Post by anachronist on 2009-09-02
According to this bug report:

[https://bugs.kde.org/show_bug.cgi?id=203885](https://bugs.kde.org/show_bug.cgi?id=203885)

The bug is already fixed in KNetworkManager, but Kubuntu packaged an older version of the software. I'm going to look into compiling the source, but I prefer not to do that since then I won't get updates.

---

### Post by xvila on 2009-09-02
Hi ! 
I think it's fixed for me (recent upgrade to KDE 4.3.1 on Jaunty)

Un-enabling and re-enabling wireless did NOT work for me

Also,

```
apt-get update
apt-get dist-upgrade
```

 did NOT show any new (hopefully fixed !) version

So, I just ...

```
apt-get remove knetworkmanager
apt-get install knetworkmanager
```

... and now it works (with, apparently, an old version)

When removing knetworkmanger, plasma-widget-networkmanagent and plasma-widget-network-manager were also wipped out, I wonder if they had something to do with the issue

Xavi

---

### Post by anachronist on 2009-09-03
I reinstalled knetworkmanager, too, after briefly trying Wicd again, which doesn't work well with some of the different network types I regularly connect to.

Instead of the newer, broken knetworkmanager, I was greeted by an older version. Still, it looks fine (not quite as nice), but most importantly, works without crashing.

I'm guessing they decided to just repackage a known, older working version for now since the crashes were a real show-stopper.

---

