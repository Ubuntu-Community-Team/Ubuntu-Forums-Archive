---
title: "Internet connection w/Live CD?"
date: 2005-12-09
forum: General Help
---

### Post by Kapungu on 2005-12-09
I booted up with live cd, but I can not seem to connect to the internet.
I have a wireless laptop and do not know how to set up a connection.
Please help

---

### Post by maxx_730 on 2005-12-09
Do you use DHCP? If so, the problem probably is that your WLAN card isn't recognized in Linux. Unfortunately, many hardware producers still don't make linux drivers for their hardware and this problem is even worse in the wlan area because of all the different chipsets etc. You could look in System > Preferences > Network and see if your card is recognized there.

---

### Post by Lofticus on 2005-12-09
You could also try first if ifconfig or iwconfig spits out something..

On my notebook eth0 is my wired-network and eth1 my wireless...

But my wireless won't function either. I have to type modprobe -r ipw2200 and then modprobe ipw2200...

Tell us if it works so far, then I can give you the rest of the connection method

---

### Post by Kapungu on 2005-12-09
[QUOTE=Lofticus]You could also try first if ifconfig or iwconfig spits out something..

On my notebook eth0 is my wired-network and eth1 my wireless...

But my wireless won't function either. I have to type modprobe -r ipw2200 and then modprobe ipw2200...

Tell us if it works so far, then I can give you the rest of the connection method[/QUOTE]

You are speaking geek linux to me.

> 
On my notebook eth0 is my wired-network and eth1 my wireless...

How do I set this up?


> 
But my wireless won't function either. I have to type modprobe -r ipw2200 and then modprobe ipw2200...

What is this about and will it make my wireless work?

---

### Post by Lofticus on 2005-12-13
> You are speaking geek linux to me.

lol

eth0 is the first ethernet device, in my case, it's my network card (the one you plug the cable in) and eth1 is the second ethernet device, in my case, it's the wireless one.

Did you already try ifconfig / iwconfig in an terminal?

Lofticus

---

