---
title: "Gnome: Networking configuration HELL!!!"
date: 2006-08-28
forum: Desktop Environments
---

### Post by viniciuscarvalho on 2006-08-28
Hello there! I've been using ubuntu for the last year, and for the last 5 months gnome (for good or bad).

Well, I'm lost with gnome connection manager, it really stinks. I transport my notebook from work <-> home.

On my job I connect using ethernet (I have a domain set up on connection properties) and through dhcp it finds out my dns servers (192.168.0.2 and 192.168.0.6).

When I get home, I use a wi-fi router but with gnome is almost impossible to connect to the wifi network, so most of the times I connect through ethernet also.

The problem is, that I have no idea why. After it connects, it keeps re-setting the connections to use my job dns' instead of mine, so I'm using the network and then I stop navigating, when I check the properties, voila... it changed the dns.

Also, defining which is the default gateway is mess, I set it to eth0, and when I click properties, eth1 is selected.

Connection on my wi-fi network? Well when IT WANTS. I tried everything. wi-fi radar (which seems to do absolutely nothing, but shows the wi-fi networks, cuz clickin on connect, it says that it has acquired it but there's no ip at all). I tried ifconfig eth1 up, down, dhcpclient and nothing nothing works. I go the networking config choose eth1, activate it (takes over then 2 minutes) and then, the signal strengh is ZERO. And then I try to boot it and it works. It ain't no hardware problem because on windows it connects smoothly.

What could be causing all this @$@#$ mess? 

It takes me over 10 minutes every f***** day, when I got on the job and when I come home, just to configure my network.

Any help would be most appreciated.

My best Regards

Vinicius

---

### Post by viniciuscarvalho on 2006-08-28
Just to add, while I was writing this message, the damn system, re-configured the network to use old dns again...

---

### Post by cptnapalm on 2006-08-28
This is what I have done, so it might work for you.

I am assuming WPA 2 for the home network.  I've had my share of headaches with dealing with WEP.  And I still don't know how I get it working.

1) apt-get install network-manager network-manager-gnome dnsmasq resolvconf

2) (It is recommended to edit /etc/network/interfaces and put comment marks '#' before ALL configurations except the lo (loop back), but I have my eth1 not commented (iface eth1 inet dhcp) and its working right now.)

3) The dnsmasq and resolvconf programs work together very nicely, in good Unix tradition.  dnsmasq is a DNS cacher and resolvconf takes care of keeping the DNS forwarders up to date.  I've never had to fool with resolvconf and the dnsmasq config file is /etc/dnsmasq.conf  (go figure ;))

Like I said, this works very well for me, both ethernet and wireless, with only WEP being something of a pain.

---

### Post by iTrendsNET on 2006-08-29
I second cptnapalm's recommendation.  Think you will be very pleased. I use that as the default setup on all my computers.

---

