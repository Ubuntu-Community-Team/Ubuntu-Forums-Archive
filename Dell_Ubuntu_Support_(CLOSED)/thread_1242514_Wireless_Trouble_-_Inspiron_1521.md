---
title: "Wireless Trouble - Inspiron 1521"
date: 2009-08-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tfrizz on 2009-08-17
I haven't used a wireless connection since upgrading to 8.10 (can't go to 9.04 due to compatibility issues for work). I played around yesterday and today, and have managed to get connected to my router. DHCP assigns properly, and I can see from both the laptop & router that they know they are connected to each other.

The problem I'm having is I can't access ANYTHING. Even pinging my router (192.168.0.1) returns DESTINATION HOST UNREACHABLE. I followed the steps at [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%201:%20All%20BCM43xx%20-%20Install%20NDISWrapper%20and%20Blacklist%20Native%20Driver](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%201:%20All%20BCM43xx%20-%20Install%20NDISWrapper%20and%20Blacklist%20Native%20Driver) 

Any help is much appreciated.

---

### Post by Ron_P on 2009-08-20
I also have a Dell 1521. Not sure what you mean exactly by "can't access anything".
After I installed Ubuntu 8.10 I do an update immediately to get the latest updates and fixes. Also make sure you have your Broadcom card is enabled under Windows .

After updates are completed and I rebooted wallah, I had a wireless connection to my router. You also need to fill in your wireless connection information. This is your network name , and security. 

Do not use the propietary drivers, on the update Ubuntu should recognize your card and install Broadcom B43 wireless driver Use this. Activate it and Deactivate any propietary drivers. 

I assume that you are using your Dell as a dual boot machine. Do you have a connection to your wireless router in Windows ? If so than you should'nt have much difficulty getting connected with Ubuntu. It went really smooth for me.

---

