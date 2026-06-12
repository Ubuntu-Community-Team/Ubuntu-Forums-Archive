---
title: "netapplet doesn't show the signal strenght"
date: 2005-04-10
forum: Desktop Environments
---

### Post by ploum on 2005-04-10
Hi,

I've installed netapplet on my laptop with a Wifi card : 
3Com Corporation 3CRWE154G72 - rev1 ( 0280:10b7:6001)
Prism54 Chipset.

It works out of the box.

Netstatus applet show me the signal strenght. (ans seems a bit too optimist, IMHO. often 100%, never under 70%. On Win98, the cards report between 30 and 70%)

Netapplet works perfectly (I can see ESSID with a little lock. I've seen once another ESSID) except that it always show a 0% signal strenght.

I don't understand why nor how to solve the problem. Any idea ? Must I report a bug against the package ?

---

### Post by sharingan on 2005-04-17
[QUOTE=ploum]Hi,

I've installed netapplet on my laptop with a Wifi card : 
3Com Corporation 3CRWE154G72 - rev1 ( 0280:10b7:6001)
Prism54 Chipset.

It works out of the box.
[/QUOTE]

Hi!!

i think i do have the same card, but i'm not able to make it work "out of the box".
the prism54 module is loaded, but there is no way to get signal, neither a connection.

this is what i got in syslog:

[FONT=Courier New]Apr 17 17:48:05 localhost kernel: eth1: resetting device...
Apr 17 17:48:05 localhost kernel: eth1: uploading firmware...
Apr 17 17:48:05 localhost kernel: eth1: firmware version: 1.0.4.3
Apr 17 17:48:05 localhost kernel: eth1: firmware upload complete
Apr 17 17:48:06 localhost kernel: eth1: no 'reset complete' IRQ seen - retrying
Apr 17 17:48:07 localhost kernel: eth1: no 'reset complete' IRQ seen - retrying
Apr 17 17:48:07 localhost kernel: eth1: interface reset failure
Apr 17 17:48:07 localhost kernel: prism54: Your card/socket may be faulty, or IRQ line too busy :(
Apr 17 17:48:08 localhost dhclient: sit0: unknown hardware address type 776
Apr 17 17:48:08 localhost dhclient: Listening on LPF/eth1/00:30:b4:00:00:00
Apr 17 17:48:08 localhost dhclient: Sending on   LPF/eth1/00:30:b4:00:00:00
Apr 17 17:48:08 localhost dhclient: Sending on   Socket/fallback
Apr 17 17:48:08 localhost dhclient: receive_packet failed on eth1: Network is down
Apr 17 17:48:12 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Apr 17 17:48:12 localhost dhclient: send_packet: Network is down
Apr 17 17:48:17 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
Apr 17 17:48:17 localhost dhclient: send_packet: Network is down
 [/FONT]

the only way i have to use this card is using ndiswrapper.

could it be that the card is not the same? how do you get the *0280:10b7:6001* number?

thnx for any info!

---

### Post by speedman on 2005-04-17
[QUOTE=sharingan]could it be that the card is not the same? how do you get the *0280:10b7:6001* number?[/QUOTE]

In a term:

cardctl ident


Regards,

SM

---

### Post by ploum on 2005-04-17
or another way is to see which PCI port your card use with :

lspci 

Then look at this entry in :

lspci -n

---

