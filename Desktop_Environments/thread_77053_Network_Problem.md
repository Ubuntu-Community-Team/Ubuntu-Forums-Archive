---
title: "Network Problem"
date: 2005-10-16
forum: Desktop Environments
---

### Post by desperate_cry on 2005-10-16
Hi,

With installed system and with live cd i can't open webpages but still connection seems to be alive. I can login to router and see other machines on LAN but i can not open webpages.

I tried to configure network (Administration>Networking) by hand, but configuration settings seems to be all correct.

What do you think the problem is?

Thanks!..

---

### Post by Zotova on 2005-10-16
A long shot, but in the network settings System>Administration>Networking is your gateway setup right? Normally it should be something like 192.168.1.1 (or whatever your router address is).

Also can you ping any websites from terminal?

---

### Post by desperate_cry on 2005-10-16
Gateway is 192.168.1.1 and i can ping websites. Then problem could be DNS servers maybe?

---

### Post by desperate_cry on 2005-10-16
No more suggestions?

---

### Post by desperate_cry on 2005-12-24
Hi,

After a long time i uninstalled the Ubuntu 5.04 from my PC, i reinstalled the version 5.10 and i have still problems about internet connection.

Anyone can help me about the problem?

---

### Post by NewbieNik on 2005-12-24
[QUOTE=desperate_cry]Gateway is 192.168.1.1 and i can ping websites. Then problem could be DNS servers maybe?[/QUOTE]

Sounds like you're spot on. A quick test would be to ping bbc.co.uk and see if it resolves the IP address (Should be 212.58.224.131)
If it doesn't mention that address try pinging it directly. So, try this in the terminal:-

ping bbc.co.uk
 
then

ping 212.58.224.131

If first fails and second succeeds, your DNS servers are not set-up correctly. Check the settings from your ISP and if that fails try using one of the BT servers on 195.12.1.1.

Good Luck

---

### Post by desperate_cry on 2005-12-24
With Network Tools, i can ping [www.google.com](www.google.com) but i can't trace... It founds the site but can not get data...
Thanks!

---

### Post by NewbieNik on 2005-12-24
[QUOTE=desperate_cry]With Network Tools, i can ping [www.google.com](www.google.com) but i can't trace... It founds the site but can not get data...
Thanks![/QUOTE]

Let me guess that the trace stops just before google and then ends with your IP? Sounds like its your router blocking port 80 traffic on the outbound.
Is there a firewall built-in to your router? Has it been altered? Check that the router is not sending traffic on port 80 to another IP address....

---

### Post by desperate_cry on 2005-12-24
I use a connection without a firewall. Also with Debian Sarge i had no problems about connection. I'm using XP to write now...

Any more ideas?

---

### Post by NewbieNik on 2005-12-24
Ony one left I can think of at the moment is Proxying, but if there's no firewall I doubt theres a proxy.

Although, if XP is connecting OK I would open the command-line and run "ipconfig /all" and copy those settings to the Linux box. Some connections tie the IP address's to the hardware address of the network card. It may be worth turning your Internet connection off and on before booting the Linux Box up.!!

---

### Post by desperate_cry on 2005-12-24
Thanks :smile:

---

### Post by desperate_cry on 2005-12-25
Hey! Maybe this topic is not hot but my problem is still hot! :)
Nobody knows where can be the problem is?
Thanks!

---

### Post by FLeiXiuS on 2005-12-25
On the router try creating a static route to your IP address.  The problem sounds as if the router doesn't know where to send local packets to your IP address, but NATing them is fine.  

I remember this problem being a huge issue in some routers with older firmware / IOS'.

---

### Post by desperate_cry on 2005-12-25
Hi,
Now sometimes i can open some (1 or 2) of the websites...
So... That's the point you write about i think... I'm using NAT, then i'll try things u sad. Thanks!

---

### Post by desperate_cry on 2005-12-25
And here is screenshots of Router config;

---

### Post by desperate_cry on 2005-12-26
Hi,

After all i found that the problem is my adsl modem. The IPv6 problem... I disabled IPv6 from FireFox and from Ubuntu default config.

I can use Firefox, but now i can not use Synaptic, Gaim, or any other applications. The connection is still null! 

What can i do about the dsl router conf?
Any ideas welcome... :confused:

---

### Post by stream303 on 2006-01-17
What does your /etc/resolv.conf show?

We can go from there...

---

