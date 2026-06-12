---
title: "Ubuntu as Gateway ?"
date: 2005-05-06
forum: Desktop Environments
---

### Post by orion_114 on 2005-05-06
I have setup my machine that connects to the internet with Ubuntu. I now need to share the internet connection with the rest of my network. I have tried setting the machines on the network up with the default gateway ip, dns servers and all that that I used to have when my gateway was windows based. It just wont seem to connect!
Am I missing something? Any help would be greatly appreciated!

---

### Post by jdodson on 2005-05-06
[QUOTE=orion_114]I have setup my machine that connects to the internet with Ubuntu. I now need to share the internet connection with the rest of my network. I have tried setting the machines on the network up with the default gateway ip, dns servers and all that that I used to have when my gateway was windows based. It just wont seem to connect!
Am I missing something? Any help would be greatly appreciated![/QUOTE]

right so we are going to need more information on your setup.  next time, run us through

1) what programs you are trying to use to set your machine up as a router
2) does anything work right?  do you have DHCP working?
3) does your ubuntu box actually work on the internet?  do you have two nics?

anyways.  i would recommend the very easy "firestarter" program to do what you need.  if you have two nics, its a breeze.  just install it via apt-get and the gui will do the rest(even configuring dhcp for you).

---

### Post by orion_114 on 2005-05-06
I have two nics. 
Configured the one with a pppoe connection to the internet. (using it now)
I got my lan running with static ip address scheme.
I haven't bothered with DHCP because it slows down my machine on bootup.
I am going to give firestarter a bash and i'll let you know if I have any glitches.
Thanks for the help! :D

---

### Post by orion_114 on 2005-05-06
thanks jdodson,
I managed to get it working. Made the blunder of selecting the eth0 as my gateway first.
Luckily firestarter has some awsome documentation.
Thanks very much for the help ! :D

---

### Post by tnadenichek on 2005-05-07
[QUOTE=jdodson]1) what programs you are trying to use to set your machine up as a router
2) does anything work right?  do you have DHCP working?
3) does your ubuntu box actually work on the internet?  do you have two nics?

anyways.  i would recommend the very easy "firestarter" program to do what you need.  if you have two nics, its a breeze.  just install it via apt-get and the gui will do the rest(even configuring dhcp for you).[/QUOTE]


hi, so i'm trying to get my computer set up as a gateway, too. i've taken the pretty common advice on installing firestarter, but i'm getting bogged down with my lan setup. i've got an oldish laptop with two pcmcia nics, which are both active, and i'm able to get a feed from the one connected to the cable modem, but i'm having difficulty sharing it through the second. firestarter gives me a handy little gague to see the trafic flow through the two nics, and the second (eth0, because of the wiring) isn't doing too much.

i'm not sure whether dhcp is working correctly, though i know that it's installed (another help area suggested installing it and, when i did, i got a handy little announcement that it was already there and i should probably not try to install something twice). when i try to enable connection sharing or connection sharing and dhcp, i get an error message that says eth1 isn't ready, which seems wierd to me since they're both active and it seems more like it should be a problem with eth0.

any suggestions?

---

