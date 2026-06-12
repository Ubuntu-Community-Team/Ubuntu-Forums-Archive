---
title: "Problem with Remote Desktop Sharing Windows to Ubuntu"
date: 2009-03-29
forum: General Help
---

### Post by nicmic921 on 2009-03-29
Ok, I am hoping someone can help me with this:

I bought a Dell Mini with Ubuntu operating systems for my grandparents who are not very computer savvy at all.  I installed real VNC so i could log on from my Window's Vista computer at home and help them if they had a problem with anything on their Ubuntu Machine.

Whe the Ubuntu machine was in my house, on my wireless network, everything worked perfectly.  I set up the Ubuntu machine to allow remote desktop sharing, i plugged in their IP address into the VNC viewer and everything worked great. Now, here's where the problem comes in.  My grandparents went home (out of state) and logged onto the computer and are hooked up to the internet.  I told them to give me their IP address (which i've confirmed is correct after asking 3 seperate people to read me the #'s) I plug that into the VNC viewer and I get the "Connection timed out (10060)" error.  

I went into my Command prompt to ping their IP address, and it comes up "destination host unreachable." So this leads me to believe there's something wrong with their IP address that's not allowing me access it in any way.  When i ping my own IP address it works and i get a response from the server.

Does anyone have any suggestions? The only thing i can think of is hat maybe I need to make their Ubuntu IP a static IP and not a DHCP?  Would that have anything to do with it?

Why would it work on my home network but then once it gets out of my network it doesn't work??? I'm very confused. Any and all help would be appreciated. Please keep in mind that though I feel like I know a decent amount about computers all this is very foriegn to me, so please try to dumb it down for me as much as possible.

Thanks again in advance for any help you can provide me with.

---

### Post by PhrankDaChickenGeek on 2009-03-29
(I'm assuming your grandparents have high-speed interned access)

You'd need to have them forward port 5900 from their cable/dsl modem to the ip address of their computer. More info for specific modems can be found here: [http://portforward.com/](http://portforward.com/)

They can find their public Internet IP (of the modem) by visiting [http://www.ip-adress.com/](http://www.ip-adress.com/), which is the IP you'd need to use from your computer. Their public IP address may change periodicity, so you'd need to check each time you want to connect. 

The reason it doesn't work is a good thing. Pretty much all modems have a firewall built in to prevent unauthorised access to computers attached to the internal network.

---

