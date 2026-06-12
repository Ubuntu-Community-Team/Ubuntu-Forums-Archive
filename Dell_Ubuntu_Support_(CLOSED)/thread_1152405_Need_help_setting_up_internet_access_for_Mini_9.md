---
title: "Need help setting up internet access for Mini 9"
date: 2009-05-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by swedishirish on 2009-05-07
I just got my new mini 9 and can't seem to configure my internet access; I'm new to Ubuntu. 
 
I have cable access from Earthlink (via Comcast cable - no Comcast account). The cable was installed for my home PC but I can't seem to get to the internet when I plug the cable into my mini 9. 
 
One friend thought the cable modem may not be recognizing the mini. He suggested trying to "spoof" the cable modem into thinking the mini was my PC by finding my MAC address on the PC and entering that somewhere in the mini. But I can't find the MAC address on my computer and don't know where this would be entered on the mini.
 
So I don't know if I'm even on the right track. Any help is appreciated so I can get to the Internet.
 
Also, would the set up be configured differently for wireless access; I'm assuming it would be. So help configuring for that would also be appreciated.

---

### Post by coffeeaddict22 on 2009-05-07
Hi, 
From what you're saying you've got two problems you need fixed.
1) the cable modem, when plugged in, doesn't give you an internet connection.
2) You can't connect to your local network using wireless.

To start with, the wired route is easiest, so fix that first.  Plug it in, open a terminal and type in ```
lshw -C network
```
as a start.  That'll give a whole heap of info; post it back here and people will know a bit more about what the problem is.
I know the terminal isn't pretty, but it's a lot easier to explain what to do when you're typing.

---

### Post by swedishirish on 2009-05-12
Will try this and post what I find. Thanks!

---

### Post by Timbers2k on 2009-05-13
Most cable modems will only allow one MAC address to connect. To get it to work for another computer, just hook up the new computer and reboot the cable modem. That is usually done by just unplugging the modem from power for a minute. You'll have to do this again to go back to your main PC.

---

### Post by ugm6hr on 2009-05-13
Wifi is easy provided you don't "hide" your SSID:
Just left-click the Network Manager icon in the top right, and then select your access point.

This is obviously different to using wired.

Is your cable modem connected by ethernet cable or USB?  How do you normally connect with it?  Can you control it from a web browser or do you need specific hardware?  What brand / model is it (and do you have a link to an online manual)?

---

