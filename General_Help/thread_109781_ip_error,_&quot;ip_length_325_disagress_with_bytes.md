---
title: "ip error, &quot;ip length 325 disagress with bytes recived 534&quot;"
date: 2005-12-29
forum: General Help
---

### Post by kise on 2005-12-29
When i try to conneckt to my network, i get this:
"ip length 325 disagress with bytes recived 534."

so i cant get a ip adress from my dhcp

So the computer says it goning to try a recorded ip, that works, so i can ping my dhcp.

But the router would not give me aksess to the internet.

Please help me..

---

### Post by FLeiXiuS on 2005-12-29
So lets start out by explaining the error.

IP length = set size of the packet determined by the sender during encapsulation
325 = IP length in bytes
Bytes receieved 534 = The resulting amount of bytes received

In more simpler terms, the IP's header is telling the receiver the packet is only 325 bytes but when the packet is sent out, the receving end is  it as 524 bytes.

Huge problem between your NIC and the router / switch.  Some one along the way is screwing up the Checksum values of the packet.  Typically it's the sender, in this case the router.  Perhaps restarting the router would sovle the problem...give that a shot.

Seeing as a DHCP packet is UDP checksum values are looked at but ignored.  Your machine is just warning you of the problem.  This shouldn't be a problem with TCP packets, but it will slower your network performance if it does effect TCP transmissions.

---

