---
title: "Networking Stops Randomly"
date: 2006-01-12
forum: General Help
---

### Post by mscman on 2006-01-12
I've looked all over on the forums and haven't been able to find a problem/solution similar to mine.  I'm running Breezy on a Toshiba laptop, which recognized both of my network cards (Marvel Yukon 88e8036 and Intel ProWireless 2200) after I disabled ACPI for them.  Now, however, the networking completely stops after time.  The time period varies each time it happens, sometimes it takes an hour, sometimes five minutes.  The only way I can get it back up and running is by a hard restart.  

I've tried using Ethereal to diagnose the problem, and all I've found is that the computer continues to send out ARP signals that don't seem to get a response.  The router and other computers also seem to respond to these.  Any help would be appreciated.

---

### Post by Mr_Grieves on 2006-01-12
The wireless troubleshooting guide:
[http://www.ubuntuforums.org/showthread.php?t=87643](http://www.ubuntuforums.org/showthread.php?t=87643)

It also seems that this thread takes up most useful tips there is:
[http://www.ubuntuforums.org/showthread.php?t=110545](http://www.ubuntuforums.org/showthread.php?t=110545)

That you're computer sends out ARP packets that goes unanswered is nothing special to worry about as long as it's not about you're router that you're connected to.
ARP is used to "glue" together the information about Network Interface Cards hardware adresses (MAC) and IP-adresses. You could say that MAC-adresses are used by Network Cards and IP-adresses by Operative Systems :) You're computer needs the information about the MAC/IP-adress connection of the next connecting IP-system, but that's all it needs :)

Most probably I think that what you're seing is probably you're router asking about other computers in you're LAN network, and not you're computer asking about information. :)
Nothing to worry about.. forget about ARP :)

---

### Post by mscman on 2006-01-14
thanks for the quick reply Mr_Grieves!  I have tried most of the things on that troubleshooting guide before; all of my networking is set up properly.  I've also been able to pinpoint the trouble to Synaptic Package Manager.  It seems that after I perform an installation using Synaptic, my networking freezes completely.  I can get around this by just using apt-get, but any advice as to why this might be occuring would be great!

---

