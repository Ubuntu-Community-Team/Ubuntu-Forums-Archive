---
title: "Wireless WMP54G Card Help"
date: 2006-05-11
forum: Desktop Environments
---

### Post by jgrauer on 2006-05-11
Hi,

I'm a new Linux user, trying to get away from Windows.  I bought a Linksys WMP54G wireless card last month, put it in my desktop, and then installed Ubuntu 5.10.  For the past week I've been navigating the forums trying to follow what other people have done to fix this same problem, but I can't seem to get anything to work.

I was able to download and install ndiswrapper and ndisgtk successfully.  When I type ndiswrapper -l, it shows me rt61 and that both the driver and the hardware are present.  However when I type iwconfig, i don't see anything with a wireless extension.  

If someone could take some patience and help me walk through this I'd appreciate it very much.

Thanks!

---

### Post by khightower on 2006-05-11
A good fix was I upgraded to 6.06 and used a dlink card

---

### Post by jgrauer on 2006-05-13
Thanks, but is there anything I can do with my setup?

---

### Post by RavenOfOdin on 2006-05-13
[QUOTE=jgrauer]Hi,

I'm a new Linux user, trying to get away from Windows.  I bought a Linksys WMP54G wireless card last month, put it in my desktop, and then installed Ubuntu 5.10.  For the past week I've been navigating the forums trying to follow what other people have done to fix this same problem, but I can't seem to get anything to work.

I was able to download and install ndiswrapper and ndisgtk successfully.  When I type ndiswrapper -l, it shows me rt61 and that both the driver and the hardware are present.  However when I type iwconfig, i don't see anything with a wireless extension.  

If someone could take some patience and help me walk through this I'd appreciate it very much.

Thanks![/QUOTE]

I have a WMP54G, and I was able to get it working about three months ago, without upgrading to 6.06 or using a D-Link card.

If your card still shows up as ra0 in the "Network" or "Network Settings" section, download the RaLink Network Configuration Utility from repositories.

My experience with the card was that as soon as I plugged it in, Device Manager picked it up as a RaLink RT8500. I'm using 5.10 so I don't know if that has anything to do with it.

You'll need to do the following for the wireless card to pick up any Internet traffic correctly (This is following a GNOME desktop):

1. Open up System > Administration > Network.
2. Where you see the box with all your connections in it the wireless, should you not have downloaded the RaLink utility and its associated files yet, may still be listed as ra0. Click on it and hit Properties.
3. In ESSID, put the name of your access point.
4. In Key Type, you can either put in Plain or Hexadecimal, choose Plain if you don't know what to use.
5. Fill out DHCP settings.
6. Tab right to the "DNS Servers" and "Search Domains" tab, fill those in with the DNS and domain of your wireless provider.
7. Right tab again to aliases, add new one and put in their default gateway with a name like "Wireless".
8. Go to Terminal and restart networking through: 

```

sudo /etc/init.d/networking restart

```

9. From that same terminal window, check if your settings are listed correctly through:

```

pico /etc/network/interfaces

```

If they are, and if your wireless shows up as good on ifconfig, then you're set.

If I think of more to add I will, gonna head out atm.

Good luck.

---

### Post by RavenOfOdin on 2006-05-13
Sorry, double post. Someone delete this please.

---

### Post by RavenOfOdin on 2006-05-13
And again, same request as above. >.<

---

### Post by RavenOfOdin on 2006-05-13
(EDIT: What the blue heck is wrong with the forum database? :eek:)

---

### Post by k420 on 2006-05-13
what is the name of the ralink network configuration tool so i can download it

---

### Post by RavenOfOdin on 2006-05-13
I think its "raconfig".

---

### Post by k420 on 2006-05-14
yeah that was not found plus also after following the advice of the wikipedia my6 cards  name switched from ra0 to eth1

---

### Post by pspotts on 2006-05-14
I've just switched to Ubuntu and use a linksys pcmcia wifi card on my laptop -- here's what I did...

After running sudo ndiswrapper -l to see that the driver and hardware were installed, I then did the following:

sudo modprobe ndiswrapper 

That got it running and wifi finally appeared as an option in Settings=>Administration=>Network, as well as when I did a sudo iwconfig in a terminal.

I still had to set the wifi preferences within Network. But once I added my network name and encryption code, all was right with the wifi world...

Hope that helps a bit...

Pete

---

