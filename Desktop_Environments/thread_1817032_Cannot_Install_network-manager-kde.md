---
title: "Cannot Install network-manager-kde"
date: 2011-08-02
forum: Desktop Environments
---

### Post by jlacroix on 2011-08-02
I recently upgraded to KDE 4.7, and it's working great, except for the fact I do not have a network manager anymore since the upgrade. I went into kpackagekit to search for it, and tried to install it (apparently the package is network-manager-kde) but it won't install, and this is what it complains about:

```
network-manager-kde : Depends: knm-runtime (= 0.9~svngit20110408-0ubuntu2) but 0.9~svngit20110728-0ubuntu3~natty1~ppa4 is to be installed

```

Am I installing the right package?

---

### Post by wildmanne39 on 2011-08-02
Hi, I believe that is the right package, but it says it depends on one package and another is going to be installed so that makes no since to me.

---

### Post by ankspo71 on 2011-08-03
Hi, 

I am using KDE 4.7.0 in Kubuntu 11.10 (alpha2 development release) and "knetwork-manager-kde" is not installed on my system, but I do have a network manager running by my clock and I believe it is the package called "plasma-widget-networkmanagement". So check to see if you have that package installed.


```
$ apt-cache policy network-manager-kde
network-manager-kde:
  Installed: (none)

$ apt-cache policy knm-runtime
knm-runtime:
  Installed: (none)

$ apt-cache policy plasma-widget-networkmanagement
plasma-widget-networkmanagement:
  Installed: 0.9~svngit.nm09.20110610.0c83d8-0ubuntu2
```

When plasma-widget-networkmanagement is installed, you can add it to the panel as a regular widget, or you can right click on the system tray, choose "System Tray Settings", (click on the unlock widgets if they are locked), then for "Display" make sure "Network Management" is enabled. When it is enabled you should see a network icon appear by your volume control icon in the System Tray. 

There should be some network options at System Settings > Network Settings > Network Connections too.

Hope this helps.

PS. When I search for network-manager-kde it says
> network-manager-kde - transitional package for plasma-widget-networkmanagement
So there might be something wrong with the dependencies in the network-manager-kde transitional package.

---

### Post by jlacroix on 2011-08-04
> **ankspo71 said:**
> Hi, 

I am using KDE 4.7.0 in Kubuntu 11.10 (alpha2 development release) and "knetwork-manager-kde" is not installed on my system, but I do have a network manager running by my clock and I believe it is the package called "plasma-widget-networkmanagement". So check to see if you have that package installed.


```
$ apt-cache policy network-manager-kde
network-manager-kde:
  Installed: (none)

$ apt-cache policy knm-runtime
knm-runtime:
  Installed: (none)

$ apt-cache policy plasma-widget-networkmanagement
plasma-widget-networkmanagement:
  Installed: 0.9~svngit.nm09.20110610.0c83d8-0ubuntu2
```

When plasma-widget-networkmanagement is installed, you can add it to the panel as a regular widget, or you can right click on the system tray, choose "System Tray Settings", (click on the unlock widgets if they are locked), then for "Display" make sure "Network Management" is enabled. When it is enabled you should see a network icon appear by your volume control icon in the System Tray. 

There should be some network options at System Settings > Network Settings > Network Connections too.

Hope this helps.

PS. When I search for network-manager-kde it says

So there might be something wrong with the dependencies in the network-manager-kde transitional package.
Thank you, that helped a lot. I think I have it figured out now. From researching after I posted the original message, it appears that Kubuntu 11.04 (without any extra repositories) provides "knetworkmanager," which I think is an actual application. The KDE 4.7 backport does not include knetworkmanager, which would explain why the package is not there anymore after upgrading. The network manager plasmoid you mentioned is available with the 4.7 backport and does work. I guess the moral of the story is if you use 4.7 you are sacrificing knetworkmanager, which I assume will be available in Kubuntu 11.10. Although I prefer knetworkmanager, the plasmoid you mentioned does work for now, and does pretty much the same thing. :)

Thank you.

---

