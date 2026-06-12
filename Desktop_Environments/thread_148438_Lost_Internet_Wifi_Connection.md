---
title: "Lost Internet Wifi Connection"
date: 2006-03-22
forum: Desktop Environments
---

### Post by BenoitD on 2006-03-22
Hi everybody,
till today, everything was perfect with Ubuntu but ... :-? 

I update my system with Synaptic; I install several applications (Amarok, mysql-server, ...) and now I'm surprised.

A new entry is placed in Grub (till ubuntu-amd64-default) and with this one I cannot connect to the net. I retried the two last commands (iwconfig wlan0 essid "mynetwork" and dhclient wlan0 but nothing appears for the first one and no connection with the secodn command.

I boot with another ubuntu-amd64 called "previous" by Grub and then I have my wifi Led flashing very slowly and I cannot connect neither.

Is there someone who has solution or clue to solve my problem ?

Many thanks,

BenoitD

---

### Post by Trance Gemini on 2006-03-22
Do you use **managed** or **ad-hoc** mode in the config that worked?
Try to switch them and see what happens (sudo iwconfig wlan0 mode ad-hoc). 

Also check if the interface is currently active.

---

