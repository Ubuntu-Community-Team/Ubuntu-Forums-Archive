---
title: "Swithching between netcards. Funny situation..."
date: 2006-02-02
forum: Desktop Environments
---

### Post by e-blade on 2006-02-02
As of recently I got a new laptop with build-in Intel PRO wireless as well as a normal/standard netcard (Ethernet 100MBits). However i do experience an annoying problem. From time to time i need to use the wireless net to get on-line (depends on  my location) so i fire it up and use it. However, with WPA-PSK, Ubuntu/Linux tends to work extremely slow, so when i get near router/switch I always plug in to get my i-net working fast again.
The problem is that apparently my wifi wont let go of the control over the netcards. I cant just "ask" for an IP for my Ethernet card, so my question is:

Is it possible to un-load ones wifi card with some shellscript and then use dhclient to obtain an IP for my other card? Perhaps there's a simpler solution but I would like to hear some suggestions.

Thanks upfront.

---

### Post by stevea1210 on 2006-02-02
Example assumes:
eth0 = wired nic  
ath0 = wireless 
(change as needed)

```
sudo ifdown ath0
```
to bring down the wireless, followed by a 
```
sudo ifuup eth0
```

to bring up the wired

---

### Post by e-blade on 2006-02-02
Thank you

---

