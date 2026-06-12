---
title: "How to disconnect from a wireless network?"
date: 2009-01-23
forum: General Help
---

### Post by andresmh on 2009-01-23
How can I disconnect from a wireless network I am already connected to without having to remove it from the list of networks?

The reason why I ask is because I am connected to a CDMA network and a WiFi network but all the traffic is going through the WiFi network and I want it to go through the CDMA. 

This makes me think, is there a way to tell some apps (eg. Firefox) to use one connection and other apps to use a different connection?

[This page]("http://brainstorm.ubuntu.com/idea/8612/") says that supposedly this has been implemented but I do not see it in my network manager.

---

### Post by timcredible on 2009-01-23
well, the easy answer is turn off wireless.

---

### Post by mempman on 2009-01-23
> **andresmh said:**
> How can I disconnect from a wireless network I am already connected to without having to remove it from the list of networks?

The reason why I ask is because I am connected to a CDMA network and a WiFi network but all the traffic is going through the WiFi network and I want it to go through the CDMA. 

This makes me think, is there a way to tell some apps (eg. Firefox) to use one connection and other apps to use a different connection?

[This page]("http://brainstorm.ubuntu.com/idea/8612/") says that supposedly this has been implemented but I do not see it in my network manager.


Maybe you can change the permission of your network device in /dev/ directory.  And start program with different user IDs so that only some of the programs can access a certain networking device.

---

