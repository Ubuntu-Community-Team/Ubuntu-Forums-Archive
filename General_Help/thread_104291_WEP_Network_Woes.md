---
title: "WEP Network Woes"
date: 2005-12-15
forum: General Help
---

### Post by tm8992 on 2005-12-15
First I'd like to say that this is probably a silly question and simple to most people around here :p

Anyway, that being said, off to my question!

I have a wireless network which I have attempted to set up using [this](http://www.ubuntuforums.org/showthread.php?t=51993) bit of information.  I set it up OK, I think, the lights came on perfectly and blinked :p  However, I was and still am bewildered by the step where you enter your keys for WEP.  The network I am connecting to is 64-bit WEP, and I have 4 keys that the router came up with from the normal passphrase.

A) Which key do I use/How do I use all 3,
B) The keys are 10 characters long; should I add dashes every four characters like some articles said?
C) What would I enter into the terminal to do this, or would I be able to do it through the network manager?

Thanks for your help :p
Tim
[SIZE="1"]Netgear Hater[/SIZE]

---

### Post by Lambert on 2005-12-15
> A) Which key do I use/How do I use all 3, key one is used by default but you can specify what key is used. Open this file

sudo gedit /etc/network/interfaces

and you should have an entry like this.

iface ath0 inet dhcp
wireless-essid 123456789
wireless-key1 123456789
wireless-key2 987654321
wireless-key3 543219876
wireless-defaultkey 2
wireless-keymode [open | restricted] (pick one depending on your setting so actual line would look like next)
wireless-keymode open
auto ath0

I do not fully understand how this works and why there is a default key but it's what I've read. Maybe somebody else can clarify this.

> B) The keys are 10 characters long; should I add dashes every four characters like some articles said?

I don't use dashes in my key but I believe it does make a difference with some routers. If you can't associate with your router come back and add the dashes

> C) What would I enter into the terminal to do this, or would I be able to do it through the network manager? 
I don't use network manager so not sure there but you can do this through the terminal with the command iwconfig.

the command would look something like this

sudo iwconfig wlan0 essid _____ key [1] _______ key [2]_______ commit

there are other options here which you can look in the man page.

man iwconfig

---

### Post by tm8992 on 2005-12-16
Thanks a million times over :P

I always knew I loved Linux-ers :D

---

