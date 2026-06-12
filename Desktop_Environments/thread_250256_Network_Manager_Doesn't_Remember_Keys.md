---
title: "Network Manager Doesn't Remember Keys"
date: 2006-09-03
forum: Desktop Environments
---

### Post by gpierce on 2006-09-03
Hello all!

I have just encountered this unusual problem. I had to do a hard shutdown of my laptop and when I restarted Network manager wouldn't restart without my entering my network key again. To make matters worse it has not recovered its memory. I started nm-applet in a console and I get this error message:

** (nm-applet:5382): WARNING **: Error saving passphrase in keyring.  Ret=6

I have tried uninstalling and re-installing network-manager and the same situation is present. Any thoughts on the source of the problem and its remedy would be appreciated.

Greg

---

### Post by gpierce on 2006-09-03
I have just noticed that gnome-keyring-daemon consumes 1.7GB of resident memory and 86% of CPU resources while it is trying to store the passphrase! I haven't seen this kind of behavior since beagle-0.2!

Greg

---

### Post by cptnapalm on 2006-09-03
To rag further on network-manager-gnome, it is so braindead on my laptop that if I go somewhere that uses WEP, it can't cope.  I have to hand edit /etc/network/interfaces and add eth1, then sudo /etc/init.d/networking restart, then use the other network configuration program. On those occasions that I have turned off my wireless to save battery and turn it on, network manager does not ever wake up from its "no wireless" mode.  I have to manually restart networking.

<OldCodgerRant>Back in the day, *nix users may have had to use command line tools for dial up or ethernet.  But they *always* worked.  I swear I'm seeing the Windozing of Linux.  *sigh*</OldCodgerRant>

---

### Post by gpierce on 2006-09-03
It used to work pretty well for me. It occasionally failed to detect networks when waking from sleep on my laptop, but overall, I think NM is a step in the right direction. If I could restore things to the way they were I would be happy.

---

### Post by orb9220 on 2006-09-04
Others I believe are using wifi radar which allows you to create profiles  for different ssid's.

---

### Post by gpierce on 2006-09-04
I have used wifi radar. It works, but the great feature of NM is that it worked with WPA networks as well and when it works NM is very useful.

---

### Post by Atomic Dog on 2006-09-04
> **cptnapalm said:**
> To rag further on network-manager-gnome, it is so braindead on my laptop that if I go somewhere that uses WEP, it can't cope.  I have to hand edit /etc/network/interfaces and add eth1, then sudo /etc/init.d/networking restart, then use the other network configuration program. On those occasions that I have turned off my wireless to save battery and turn it on, network manager does not ever wake up from its "no wireless" mode.  I have to manually restart networking.

<OldCodgerRant>Back in the day, *nix users may have had to use command line tools for dial up or ethernet.  But they *always* worked.  I swear I'm seeing the Windozing of Linux.  *sigh*</OldCodgerRant>

Wifi radar will do you up good.  Try it, you'll like it.

---

### Post by orb9220 on 2006-09-04
Yeah when mine stopped working I went gedit /etc/network/interfaces and looked there and for some wierd reason it had added lines. 

#iface ath0 inet dhcp 
#wireless-essid [www.personaltelco.net](www.personaltelco.net) which I had to comment out to get it working again.

---

