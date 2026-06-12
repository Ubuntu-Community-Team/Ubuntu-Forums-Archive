---
title: "using crossovercable in UBUNTU"
date: 2005-05-07
forum: Desktop Environments
---

### Post by Janissary on 2005-05-07
I have 2 PeeZee's running both ubutnu and winXp 

I am currently using a crossover cable for networking,

On WinXP everything works fine, but when I open ubuntu on gateway comp. client fail to connect internet,

how can I set up a crossover connection to share internet connection in ubuntu?

thanks for helping to a newbie :) !

---

### Post by derrick1985 on 2005-05-07
[QUOTE=Janissary]I have 2 PeeZee's running both ubutnu and winXp 

I am currently using a crossover cable for networking,

On WinXP everything works fine, but when I open ubuntu on gateway comp. client fail to connect internet,

how can I set up a crossover connection to share internet connection in ubuntu?

thanks for helping to a newbie :) ![/QUOTE]

Well, first of all how are you connecting? Is your other PC on? Are you getting an IP through DHCP (automatically) or is it a static one (you set it up yourself?)

---

### Post by Janissary on 2005-05-07
[QUOTE=derrick1985]Well, first of all how are you connecting? Is your other PC on? Are you getting an IP through DHCP (automatically) or is it a static one (you set it up yourself?)[/QUOTE]
 I'm using cable connection and getting IP through DHCP,

on my local network I give 192.168.0.1/255.255.255.0 to main pc
and 192.168.0.2/255.255.255.0 to client, 

but I think problem is here, in windows there was an option like share this internet connection on your lan, but I cannot do this on Ubuntu!

---

### Post by Janissary on 2005-05-08
[QUOTE=Janissary]I'm using cable connection and getting IP through DHCP,

on my local network I give 192.168.0.1/255.255.255.0 to main pc
and 192.168.0.2/255.255.255.0 to client, 

but I think problem is here, in windows there was an option like share this internet connection on your lan, but I cannot do this on Ubuntu![/QUOTE]
 up

---

### Post by psoleko on 2005-05-08
Do you have a modem connection you are trying to share?
Ubuntu can share a connection just as well as Win XP albeit it takes a bit more work.

---

### Post by az on 2005-05-09
[QUOTE=Janissary]I'm using cable connection and getting IP through DHCP,

on my local network I give 192.168.0.1/255.255.255.0 to main pc
and 192.168.0.2/255.255.255.0 to client, 

but I think problem is here, in windows there was an option like share this internet connection on your lan, but I cannot do this on Ubuntu![/QUOTE]


The Ubuntu box is the gateway?  Yes, you will need to share the internet connection.  Install firestarter and enable the Network Address Translation (NAT is connection sharing)  You will also need to share dns.  Offhand, I am not sure how firestarter handles this.

---

