---
title: "Configuring Ubuntu"
date: 2008-12-18
forum: General Help
---

### Post by jakestan on 2008-12-18
Hey All,

just installed Ubuntu (not ubuntu mobile) on my eee pc which I bought this morning.  It originally had windows on it but I wanted a laptop which had ubuntu linux on it so I could begin learning.  Couple of things...

How do I know if the wireless card is working?  I couldnt see my wireless network at home so was wondering if there was a way to install the driver for this card.

Secondly, the SDHDC/ SD card slot.  I was unable to find the card on the system when I put one in full of my holiday photos.

Other then that everything else is working fine.  I've got audio, video, blluetooth is working perfectly, ive got the OS configured just how I want it...it's just these 2 little issues.

Many Thanks

JakeStan

---

### Post by lovelyvik293 on 2008-12-18
First of all welcome to ubuntu world.
One advice please always post the version of ubuntu you are using.

For wireless use
```

lspci|grep Wireless

```

---

### Post by donkyhotay on 2008-12-18
Although the built-in networking system does pretty good I've had better luck configuring wireless cards through wicd instead.
```
sudo apt-get install wicd
```
Admittedly this is assuming the hardware is working correctly which the previous post will help determine.

---

### Post by jakestan on 2008-12-18
thanks for the info guys.

Running Ubuntu 8.10 on this machine.  however, when i type

lspci |grep wireless 

i get no output.  Also when I use the other command suggested it pops up suggesting it couldnt find the correct package.

regards

jakestan

---

