---
title: "Bullet-proofing Kubuntu"
date: 2010-05-14
forum: Desktop Environments
---

### Post by gobble on 2010-05-14
Hello All

I just wanted to list a few pain points on 10.0.4 which I've been using since the launch day now. I migrated from XUbuntu 9.0.4.

1. During my first install attempt, I lazily clicked on a window minimize button. Poof! All my feedback was gone!! An instant later I think the installer began downloading language packs taking over 15 mins on my connection. I had no clue, searched around in the console, thought the installer had hung and restarted the install from scratch!! 

Commonsense tells me that the buttons to minimize or maximize or kill a window need not be there during an install since one is not expected to multi-task during an install. Wonder how it never occurred to anyone in the community so far.

2. I was never prompted for network DNS settings during the install and forgot about it. I have been suffering slow DNS and surfing for last few weeks because of this without realizing I had forgotten to configure my DNS server settings (escalated to ISP then realized my folly!  :)). My system makes a multicast query to locate a DNS, finds one then resolves a domain after 2 or 3 secs.  Worse - KNetworkManager does not launch for me at all!! I manually added the dns servers to the /etc/resolv.conf but it vanishes after each  reboot! I am still stuck with slow browsing 10 days after install. 

It is amazing that a new release can be so fundamentally broken that one cannot launch a network manager to configure basic settings, or that an installer does not prompt for basic settings to ensure smooth functionality of what matters the most to any user in the world today- The Internet!!  The testing procedure needs to be more robust I guess or am I the only person suffering this?


3.  The KDE taskbar does not allow me to add shortcuts to my favorite apps like Firefox to access with a single click!! Wow! This is so complicated that I now have to learn how to do simple things taken for granted differently?!!  :confused:

This is 2010. When will Ubuntu really Rock?!! :guitar:

I suffered all previous  releases over last 10 years regarding graphics capability (not the fault of FOSS but the h/w vendors) because of my commitment to FOSS ( Finally purchased this year a $325 HD player to work with my $700 monitor when I don't need a dedicated player - rather than a $100 Windoze licence - *after not watching movies on my desktop for last 5 years out of frustration!!*). The Ubuntu community is doing great work I have to say but still an end-user has to suffer it in the end. Hard for me to recommend to a Windows user even today in 2010!! 

Regards

---

### Post by sakisds on 2010-05-14
1) Minimazing the installer works fine for me. 
3) You can add shortcuts anywhere on the panel with a simple drag-and-drop from the menu. You could also add a new panel for shortcuts.

Edit: If the network problem is a matter of a file replace you could make a copy of the working resolv.conf and put something like this to the kde startup:
```
cp /etc/resolv.conf.fixed /etc/resolv.conf
```

---

### Post by gobble on 2010-05-15
I navigated to network settings from Systems Settings (dont know if this launches knetworkmanager) and added DNS settings and a manual IP address for Wired Ethernet connection. After a few reboots I have confirmed that it does not take effect!! 

This is getting unbelievably fantabulous!! :guitar: A Linux version that cannot launch a network manager or accept settings given to it via other means!!  

Stating a preference like some people have no personal problems with minimizing windows during install is missing the point. I want to stress this ask is about bullet-proofing it not about demanding features that catch somebody's fancy.

Regards

---

### Post by gobble on 2010-05-15
I navigated to network settings from Systems Settings (dont know if this launches knetworkmanager) and added DNS settings and a manual IP address for Wired Ethernet connection. After a few reboots I have confirmed that it does not take effect!! 

This is getting unbelievable!! :guitar: A Linux version that cannot launch a network manager or accept settings given to it via other means!!  

Stating a preference like some people have no personal problems with minimizing windows during install is missing the point. I want to stress this ask is about bullet-proofing it not about demanding features that catch somebody's fancy.

Regards

---

### Post by gobble on 2010-05-15
> **sakisds said:**
> 1) Minimazing the installer works fine for me. 
3) You can add shortcuts anywhere on the panel with a simple drag-and-drop from the menu. You could also add a new panel for shortcuts.

Edit: If the network problem is a matter of a file replace you could make a copy of the working resolv.conf and put something like this to the kde startup:
```
cp /etc/resolv.conf.fixed /etc/resolv.conf
```

Thats a kludge I am unwilling to do on each reboot or write a script for. Its plain stupid way to do it. Sorry dont mean it against you personally. The idea is repulsive thats all.

Drag and drop does not work. Tried it a few times. Any other ideas?

Regards

---

### Post by kio_http on 2010-05-15
> **gobble said:**
> Thats a kludge I am unwilling to do on each reboot or write a script for. Its plain stupid way to do it. Sorry dont mean it against you personally. The idea is repulsive thats all.

Drag and drop does not work. Tried it a few times. Any other ideas?

Regards

On kde-look.org, there is a plasmoid for the quicklaunch functionality from KDE3.

---

### Post by ankspo71 on 2010-05-15
Hi,
In Kubuntu, if your panels are locked, unlock them by right clicking on the panel then selecting "unlock widgets". When they are unlocked, go to your start menu and right click on any application and choose "add to panel". 

To move the new shortcut to the correct location on the panel, right click on the panel then select Panel Options > Panel Settings, then drag the shortcut to your preferred location on the panel. 
Hope this helps.

---

### Post by sakisds on 2010-05-15
> **gobble said:**
> Thats a kludge I am unwilling to do on each reboot or write a script for. Its plain stupid way to do it. Sorry dont mean it against you personally. The idea is repulsive thats all.

Drag and drop does not work. Tried it a few times. Any other ideas?

Regards

Don't worry, no offense taken ;). I know that idea wasn't a permant solution but it could help until you/someone thinked something better. Also about the panel shortcuts, try right-click on desktop > Unlock Widgets and then drag and drop from the menu.

About the installer, I know what you mean, I had the same problem today in a vm. Kubuntu is a nice os but it has rough edges.

---

