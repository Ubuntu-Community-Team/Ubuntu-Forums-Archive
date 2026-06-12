---
title: "No Internet after Dapper upgrade"
date: 2006-06-12
forum: Desktop Environments
---

### Post by Wetscoast Gus on 2006-06-12
Absolute newbie here. I upgraded from Breezy to Dapper over the weekend, and once I installed Dapper, I could no longer connect to the Internet. Everything worked fine in Breezy and WinXP, and it continues to work using the Dapper live CD.

I installed Breezy (clearing the HD first) from a mailed disc I got several months ago, then downloaded and installed Dapper.

I use BellSouth DSL with a Westell modem, if that matters, though it appears others are having similar issues with different hardware.

Thoughts?

---

### Post by irv on 2006-06-12
System>Administration>Networking
Select your network card or modem, then properties and make sure there is a check mark in Enable this connection.

---

### Post by Wetscoast Gus on 2006-06-12
Enable is checked. Still doesn't work.

---

### Post by deavik on 2006-06-12
At what stage does the internet not work? Do you have a dialup or eth connection?

There are programs like pppoeconf which can help configure your router/modem - to fine-tune it you may have to tweak /etc/network/interfaces manually also.

---

### Post by Wetscoast Gus on 2006-06-13
When I boot Dapper from the hard drive, the net doesn't connect. It's a DSL connection through an ethernet card.

---

