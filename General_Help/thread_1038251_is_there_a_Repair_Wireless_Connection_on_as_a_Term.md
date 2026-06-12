---
title: "is there a Repair Wireless Connection on as a Terminal Command?"
date: 2009-01-12
forum: General Help
---

### Post by sendblink23 on 2009-01-12
I do have Wireless connection with Ubuntu

I'm just wondering since I many times having connection, sometimes when surfing around the web... any clicking to any link or placing a new website in the address bar ...  it just stays Loading and nothing happens...  not even Refresh

What Command for Terminal would Repair your Wireless Connection, as an example in Windows XP, you just right click your wireless connection icon, and you will see the option Repair Wireless Connection.

Is there a way to do that on Ubuntu?

I also tried clicking the wireless icon on Ubuntu & selecting again my wireless connection, but it stays *searching to connect .. and it never connects*,  I have to right-click *wireless icon*.. un-mark(disable) Wireless connectivity, and re Enable Wireless connectivity too have it working again...  I'm tired of having to do that...  when that issue happens to me  while browsing around the internet.

.. so yeah .... ?  :)

THNX

---

### Post by rbc on 2009-01-12
I do not know what the "Repair" actually does in Windows, but how about:
sudo /etc/init.d/networking restart

---

### Post by sendblink23 on 2009-01-12
> **rbc said:**
> I do not know what the "Repair" actually does in Windows, but how about:
sudo /etc/init.d/networking restart

I'm not sure if it did what it was suppose to but I got this:

> 
 * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.
                                                                         [ OK ]



If it occurs to me again.. while surfing around..  I'll try that command to see if it helps

---

### Post by sendblink23 on 2009-01-12
Any other Terminal Commands, are welcomed, if that isn't the only one around..  for Repairing the Wireless Connection

---

