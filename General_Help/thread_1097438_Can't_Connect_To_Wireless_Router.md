---
title: "Can't Connect To Wireless Router"
date: 2009-03-16
forum: General Help
---

### Post by Patriot1776 on 2009-03-16
Alright, I earlier tonight installed Hardy Heron LTS on my brother's Acer laptop that does have wireless and Bluetooth capability.  Bluetooth seems to work, but the laptop is having problems connecting up to a router, both wired and wireless.

I installed Ubuntu on it at my house, that has a plain DSL modem for internet connectivity, and using that modem and my desktop's ethernet cable, got the laptop to connect via pppoeconf and downloaded and installed all the upgrades needed to take it from the LiveCD version 8.04.1 to 8.04.2, with the current kernel of 2.6.24-23-generic.

However, later when I took the laptop to the brother's house, where he has a router for a home LAN, the laptop was seeing the wireless hardware as I was seeing wlan0 in the network settings, but I couldn't get it to connect to the wireless router.  I also tried a wired connection to the router, and still no luck, pppoeconf was useless.  What am I doing wrong?

Other than the internet problems and the as-always multimedia headaches when freshly installing Ubuntu on a system, I think I did pretty darn good installing Hardy on a laptop without wiping out my brother's Windows-data.  He's wanting to transition to Linux gradually to keep from having to buy anti-virus software, for stability reasons, and also to keep from having to buy Windows Vista or Windows 7.  I'm sure the internet issues are easily solvable, as Ubuntu knows the wireless hardware is there and I can enable and disable it, I just need some guidance on getting Ubuntu to connect to the router using it.

---

### Post by ramjet_1953 on 2009-03-16
I have an Acer TravelMate 4101.
I'm not sure what wireless card your Acer has, but mine uses the ipw2200 driver.

All I had to do was to open an editor in sudo mode and create a file in /etc/modprobe.d/ called ipw2200:

ie:

```
sudo nano /etc/modprobe.d/ipw2200
```

I then added this line to the file:

```
options ipw2200 led=1
```

and then saved the file.

If course, if your particular wireless card is different the ipw2200 statement will need to be changed to reflect the card.

The way to check on the model of your wireless card is to do the following:

Navigate to [COLOR="Blue"]Applications>Accessories>Terminal
[/COLOR]
Copy and paste this command into the terminal:

[COLOR="Red"]sudo lshw -C network[/COLOR]

The second line should identify your wireless card's hardware model number.

Once this is done, you should find that when you press the wireless button on your laptop, the card will power-up and the LED will indicate activity.

Regards,
Roger :D

---

### Post by Patriot1776 on 2009-03-16
Ramjet, this Acer laptop has the Intel 3945abg wireless chipset or card in it.  So, how would that change the little procedure you posted?

---

### Post by Patriot1776 on 2009-03-16
Ramjet, it didn't work, it actually make things even worse.

On the other hand, I did find out what driver I have: iwl3945 is what the lshw command gave me as the driver and module in use.  Setting "led=1" in modprobe.d actually made it where I couldn't enable and disable it.  Anybody got any other ideas?

---

