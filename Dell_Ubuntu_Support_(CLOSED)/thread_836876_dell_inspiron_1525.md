---
title: "dell inspiron 1525"
date: 2008-06-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by taekwondosnw on 2008-06-21
ok, i'm sure there are many posts about this but i have a dell inspiron 1525 with a dell 1395 802.11G wireless mini card. i can't seem to be able to connect to the internet with it.

is there a simple code i could type into terminal to get it to work?

if not would buying this < [http://www.amazon.com/Orinoco-Gold-802-11b-Wireless-Card/dp/B00006BA7X](http://www.amazon.com/Orinoco-Gold-802-11b-Wireless-Card/dp/B00006BA7X) > solve my problem? i have been meaning to buy a new card anyway. < Orinoco Gold 802.11b Wireless PC Card >

---

### Post by stats on 2008-07-07
the driver is in the repo now
if you dint install  ndiswrapper then skip steps 2,3,4 
1.Update & upgrade using update-manager/synaptic/adept etc
2.
```

sudo apt-get remove ndisgtk ndiswrapper-common ndiswrapper-utils-1.9

```
3. Remove the ndiswrapper line from /etc/modules
4. Disable wireless from the network manager applet and then

```
sudo modprobe -r ndiswrapper
```

If it cribs about module being in use, it means you have not disabled wireless
5. Restart, if there were any kernel upgrades
6. System->Administration->Hardware Drivers
I see a wl driver here. Make sure it says enabled and is in use.

worked for me with dell 1395 on inspiron 1525

---

