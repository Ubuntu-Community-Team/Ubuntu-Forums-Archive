---
title: "A few questions. Help Needed."
date: 2006-04-09
forum: Desktop Environments
---

### Post by Pedricko on 2006-04-09
Hi guys and gals.

Okay, I've got a pretty low key ubuntu set up (128mb, SFF style compaq with a 10GB hardrive) here and I was thinking of a few upgrades.

First off, I have just aqquired a 21inch CRT (to replace my early philips 15inch flat screen with literally a 2.5inch bezel), will X automatically format to the highest possible resoloution? if not how would I do this?

Also will ubuntu be ok if I add an extra 128mb of ram? the highest this system supports is 512k. I'm sure I've read ubuntu doesnt plug-n-play... - but dont worry this system is going so for my pimptastic custom system!

Last question (mainly for UK users) - can I network an ubuntu system and a windows ME system to share internet and printer capabilites? The router I'm using is the BT 210 that came free with the subscription - both computers have a ethernet port, will I need extra hardware? Please help.

Sorry for my newbish questions - I'm very unxpericned when it comes to networks!

---

### Post by kingmonkey on 2006-04-09
Adding extra RAM will cause no problems.

The answer to the network question is basically "yes". Ill need to know more about your router and what cables and what type of printer you have to answer futher.

In regards to the monitor, X will not automatically go to the highest resolution, you will need to issue a command that will reconfigure x for you.

---

### Post by Pedricko on 2006-04-09
[QUOTE=kingmonkey]Adding extra RAM will cause no problems.

The answer to the network question is basically "yes". Ill need to know more about your router and what cables and what type of printer you have to answer futher.

In regards to the monitor, X will not automatically go to the highest resolution, you will need to issue a command that will reconfigure x for you.[/QUOTE]

the router has outgoing ports for ethernet (connected to this computer) and one free for USB, however the other windows ME based computer will be quite some distance (10m +) away.

How will I get X to the highest resoloution which is 1600x I believe.

---

### Post by Omnios on 2006-04-09
For the monitor you should connect it and boot up in recovery mode as this will sidestep any monitor problems such as over frequency etc. In command line type  ```
sudo dpkg-reconfigure xserver-xorg
```. Go thought the turtle like grapical thing and you should be all set. Advise writing down your frequency ranges etc to check them or just do a simple monitor choice and choose the big monitor size.

---

### Post by kingmonkey on 2006-04-09
Sounds like you will only need some network cable then to reach your windows computer.

I think to reconfigure X is:
dpkg-reconfigure xserver-xorg

---

### Post by Pedricko on 2006-04-09
when the new memory arrives, I may just reinstall breezy, that way I can set it for the new screen etc, then handle the network.

Sorry if im inconherent - I've had far to much cider.

---

