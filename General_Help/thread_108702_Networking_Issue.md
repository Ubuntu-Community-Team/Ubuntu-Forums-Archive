---
title: "Networking Issue"
date: 2005-12-26
forum: General Help
---

### Post by Helfax on 2005-12-26
I've stumbled across an odd problem. I'm running Ubuntu 5.10 which works fine and can get on the network, etc. However, other systems on the network are unable to ping this system UNLESS it pings them first. Strange? I thought so too. I thought that it might be a routing issue or something like that so I added a post-up line in /etc/network/interfaces to ping both the gateway and localhost. Unfortunately, this didn't seem to make a differnce. I'm not running any sort of firewall on the Ubuntu box. Any suggestions would be greatly appreciated. 

Thanks.

Helfax

---

### Post by jrb114 on 2006-01-03
I've had this issue too - and no replies from anyone else either :( 

[http://www.ubuntuforums.org/showthread.php?t=111097&highlight=firewall+ping](http://www.ubuntuforums.org/showthread.php?t=111097&highlight=firewall+ping)

Any help out there? Pls?

---

### Post by steve.horsley on 2006-01-03
All I can think of is to install ethereal and do a network capture to see what's actually happening on the LAN. Ethereal is there in Synaptic.

---

### Post by N6546R on 2006-01-03
I wonder if the 5.10 machine isn't responding to ARP requests? Ethereal is definitely your friend here.

Perry

---

### Post by jrb114 on 2006-01-03
Thanks Perry, 

You're exactly right. It isn't answering ARP requests, ethereal is showing nothing but ARP/LLC on the server, whilst ethereal on the client keeps on asking who has got the IP address. Interesting, I had absolutely no idea how machines found out where others were on networks. You learn something new every day :)

For those, like me, who have no idea what an ARP request is:

[http://en.wikipedia.org/wiki/Address_Resolution_Protocol](http://en.wikipedia.org/wiki/Address_Resolution_Protocol)

Now, what do I do about it?

James

X ---- EDIT ---- X

I've just found a previous post regarding this:

[http://www.ubuntuforums.org/archive/index.php/t-80699.html](http://www.ubuntuforums.org/archive/index.php/t-80699.html)

Although there doesn't seem to be a solution to it. It describes the problem perfectly.

For the record, I'm using 2.6.12-10-386 (and -k7), madwifi (atheros chipset) wireless running with WPA supplicant, and everything worked perfectly under hoary.

I've now changed to the wired interface, and the problem seems to have gone away. (Although it's probably too early to tell just now.)

X ---- End edit ---- X

---

