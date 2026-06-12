---
title: "Problem with tcpdump"
date: 2009-03-12
forum: General Help
---

### Post by minotauro on 2009-03-12
Hello to all of the forum. 
Using aircrack-ng I have completed the ChopChop attack with this result:


Saving plaintext in replay_dec-0312-145845.cap
Saving keystream in replay_dec-0312-145845.xor

Completed in 48s (2.94 bytes/s)


Then I have executed:

root@mamone-laptop:~# tcpdump -e -n -s0 -r replay_dec-0312-145845.cap


and I have received the answer:

reading from file replay_dec-0312-145845.cap, link-type IEEE802_11 (802.11)
14:58:45.892678 DA:00:12:17:65:07:cf BSSID:00:17:c2:81:64:61 SA:00:17:c2:81:64:5d LLC, dsap SNAP (0xaa) Individual, ssap SNAP (0xaa) Command, ctrl 0x03: oui Ethernet (0x000000), ethertype IPv4 (0x0800): 93.145.25.205.12486 > 192.168.1.170.55224: UDP, length 111


Why I do not find arp who-has .......... tell ...........????


Someone can help me?

Thanks

---

### Post by minotauro on 2009-03-13
But I have tried also with:
packetforge-ng -0 -a BSSID -h 00:11:22:33:44:55 \ -k 192.168.1.100 -l 
192.168.1.101 -y replay_dec-#######.xor \ -w arp-request 

or

packetforge-ng -0 -a BSSID -h 00:11:22:33:44:55 \ -k 255.255.255.255 -l 
255.255.255.255 -y replay_dec-#######.xor \ -w arp-request 


but I have always this answer:

Please specify a destination IP (-k). 
Error building an ARP packet 

I believe that the problem is already visible in tcpdump, it is normal school that us is?
ethertype IPv4 (0x0800): 93.145.25.205.12486 > 192.168.1.170.55224
and not me decoy arp who-has .......... tell .....?
Us it must be an error from some part but I do not know to find it.
Help me.

---

