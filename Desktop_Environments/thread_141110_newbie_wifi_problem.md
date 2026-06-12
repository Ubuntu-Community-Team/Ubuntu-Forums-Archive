---
title: "newbie wifi problem"
date: 2006-03-07
forum: Desktop Environments
---

### Post by wilryt2 on 2006-03-07
I am an utter beginer with linux, so please bare with me.

I have just installed Kubuntu Breezy Badger onto a Dell Inspiron 9300.  I have a built in wireless card (Intel Pro Wireless 2915 (im pretty sure, tell me how to look it up for sure and I will ;-)  )).   

The card is recognized and I'm pretty sure I have it setup correctly, but everytime I go into the system settings, it says eth1 is disabled.  eth0 is my hardwired lan and it works fine (hence me posting haha).  My current settings are:

IN System Settings:
Automatic   -   DHCP
Activate when the computer is rebooted.

ESSID and WEP key are entered.
Hexadecimel Key

IN KWiFiManager

Config 1
Network name : netgear4315
Operation Mode Managed
Speed: Auto
Use Encryption
          Key to use 1
          Crytpo Mode Open
          Key is entered
Load Preset configuration on startup.
settings applied to eth1.


When I scan for networks using kwifimanager, I find them all, and kwifimanager claims to be connected to my accesspoint, but won't give me my IP address, and my netgear router doesn't show my laptop being connected via wifi (only wired).  I am highly confused.  Any help is appreciated.  If I need to give more info, I'd be happy to.  

~Will

---

### Post by wilryt2 on 2006-03-07
Oh, and when I attempt to enable the wireless connection in the System Settings windows, It quickly enables and then disables again.

---

### Post by sal on 2006-03-07
i have this same problem. i use kubuntu and the KControl wireless stuff wont work. i just use iwconfig from the command line.
hopefully in 6.04 it will be better.

---

### Post by MahRain on 2006-03-08
I had these problems, until I configured my wlan via iwconfig, told ifconfig a static ip and commented-out
> 
# iface eth1 inet


in /etc/network/interfaces.

---

