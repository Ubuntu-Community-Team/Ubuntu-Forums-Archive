---
title: "Wireless connects but no traffic."
date: 2008-01-27
forum: Dell  Ubuntu Support
---

### Post by jamesatsea on 2008-01-27
Very new to all of this.

I just bought a Dell 1420n with 7.10 installed. Fresh out the box everything seems to work great except...

My wireless connects; I receive DHCP, am assigned an IP and get IPs for DNS and Default Route. However when starting Firefox I get "Server not Found". 

I am able to see other Windows computers also connected the the same wireless network as me.

Normally when starting a web browser (on a Windows host) I get an internet sign in page but instead I get the "Server not Found".

The strange thing to me is that I can't ping the IP address for the Default Route or DNS.

Any help would be greatly appreciated.

---

### Post by apswartz on 2008-01-27
"internet sign in page"
What kind of network is this? In a coffee shop?
Have you tried other networks?

---

### Post by jamesatsea on 2008-01-27
A big floating coffee shop. :-) This is a cruise ship. The Internet Cafe Manager on board had never seen linux before so was no help.

There are 2 wireless networks one for crew and one for passengers. Once you connect and open a browser they bring up a login page for a prepaid internet card. I can connect to either network and get DHCP. I can see and connect to open shares on other computers on the network, but no interent traffic.

---

### Post by ghost_ryder35 on 2008-01-27
can you try statically assigning your ip address and DNS servers?

---

### Post by jamesatsea on 2008-01-27
Greetings ghost_ryder35.

Just tried it. Thanks for the suggestion.

Still the same issue. The networking seems to be fine in that I can connect to other computers also on the Wirless network. File sharing between computers over the wireless is no problem.

It just seems that internet traffic is a problem. So I suppose it is something to do with routing. Weird!

Any ideas?

---

### Post by ghost_ryder35 on 2008-01-27
WOW, seems like they maybe need to reboot their router :)  Good luck, if I can think of anything else I will post it.

---

### Post by jamesatsea on 2008-01-27
All the windows users around me are connecting with no problems. :-(

---

### Post by ghost_ryder35 on 2008-01-27
do you have a firewall running?  Possibly blocking the ports?  Maybe FireFox is not getting the right homepage logon webpage so it is trying to take you to your usual logon page like Yahoo or something and thats why it is failing?  Maybe you can ask them for the website (or look onto a Windows users computer) and type in the address manually into the FireFox address bar after you are connected to their wireless network.  Just a thought.

---

