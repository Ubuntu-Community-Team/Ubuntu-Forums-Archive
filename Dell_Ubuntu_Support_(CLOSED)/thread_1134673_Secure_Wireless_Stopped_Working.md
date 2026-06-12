---
title: "Secure Wireless Stopped Working"
date: 2009-04-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Ed Kura on 2009-04-23
I'm running Ubuntu 8.04 on my Mini Net 9.  It's been great, till now.  Early this week I allowed the Update Manager to install the latest updates.  Now it won't connect to my secure wireless network.  As far as I can tell, the settings have not changed.  It still connects to unsecured networks just fine.  How do I fix this?  I need my secure network back!  Thanks for any help you can provide!

---

### Post by coffeeaddict22 on 2009-04-24
Hi,
To determine the issue a little more, open a terminal and type in 
```
iwconfig
``` and then 
```
sudo iwlist scan
```
That will tell you a bit about the networks your PC can see through the card.  If you can't see any, it might be a card detection problem.
If you've changed your network at all, the issue may be with the settings.  Have a look at [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide?highlight=(\bCategoryNetworking\b)]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide?highlight=(\bCategoryNetworking\b)")
Good luck!

---

