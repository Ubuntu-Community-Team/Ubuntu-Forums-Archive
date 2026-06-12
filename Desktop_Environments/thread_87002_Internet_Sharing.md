---
title: "Internet Sharing"
date: 2005-11-07
forum: Desktop Environments
---

### Post by kapa_des on 2005-11-07
I'v got 3 network cards, one with real IP and internet from the server and the others fake IP and local ... i want to know how do I share the internet from the main card so the other cards have acces to the Internet aswell ...

---

### Post by kapa_des on 2005-11-07
plz help ....

---

### Post by mcduck on 2005-11-07
[QUOTE=kapa_des]plz help ....[/QUOTE]
Here's the easy way:

1. Check that all network cards are configured and active in System/Administration/Networking. Leave ther card connected to net use DHCP or however you connection works. Set the other ones to use static IP-adresses, like 192.168.0.1 and 192.168.0.2. Set the subnet masks to 255.255.255.0.

2. Install Firestarter, if you haven't got it yet.

3. Start the firestarter GUI (in Applications/system tools/Firestarter). Click the 'Preferences' button, then 'Network Settings', and choose your internet/local network cards, and mark the 'Enable Internet connection Sharing'.

4. Set your other machines to use static IP's (192.168.0.3 ->), and set their gateway to your Ubuntu machine's IP (192.168.0.1) with subnet mask 155.255.255.0. That's it.

Now here's the problem, I don't know if you can choose more than one local network card with Firestarter. I only got 2 cards. There also seems to be an option for using DHCP for shared connections too, but I could't get it working myself. I'm sure somebody who really knows about these things can tell you a better way to do this, but at least this should get you started..

---

### Post by psusi on 2005-11-07
My advice is to drop the $50 or so ( probably less these days ) on a hardware router.  I prefer the linksys models.  Plug it into your cable modem and your machines into it and you're set.  Quick easy sharing, and free hardware firewall.

---

