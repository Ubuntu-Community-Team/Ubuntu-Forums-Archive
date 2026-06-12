---
title: "Wireless Internet Help"
date: 2007-09-29
forum: Desktop Environments
---

### Post by maplestar on 2007-09-29
Ok, I've downloaded ubuntu using steps I found on the internet.  I have dual boot and I can load onto ubuntu.

Next comes internet.  I have no clue how to get internet.  Neither am I that good at computer hardware/software.

I've done what the guide tells me to.  I go to system -> administration-> network and I set roaming mode on my computer.  Then I add another network.

I type my network name: familywuhost
select WEP Hex...
type my key :********
then i set the authentification to sharing mode.

I wait, and pretty much nothing happens.

Help? 

Btw, I use a linksys wireless g-adapter in the computer.

---

### Post by Ongion on 2007-09-30
Ok, I have firsthand experience on how annoying this is.  I'm going to assume that your wireless card is supported.  First, go to the terminal and type "su" to log into the root environment.  Then type "iwlist scan".  This will display the wireless networks in your vicinity.  Now, if your wireless device shows up as eth1, then type "iwconfig eth1 essid  familywuhost mode managed key (Your WEP Key) channel (channel number - 1-11, usually 1, 6, or 11, default is 6).  Make sure to replace "eth1" with the location of your wireless card, as shown by iwlist.  This will hopefully get your wireless internet running.  Also, make sure roaming is disabled.

---

