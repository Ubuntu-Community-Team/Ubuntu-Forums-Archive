---
title: "getting green face in Azureus-&gt; but no byte downloaded"
date: 2005-05-30
forum: Desktop Environments
---

### Post by yccheok on 2005-05-30
Hi, I had faced this problem for several days. Previously, my router was configured to use Azureus with no problem. 

After I upgraded to latest ubuntu 5.04 and latest Azureus 2.3.0.2, I experience some problem. I have 4 torrents running, all of them are showing green face. However, even I let them run overnight, no single byte was downloaded. 

When I perform NAT test on port 6881, sometimes I will get OK result, sometimes I will get error result. 

I check my ubuntu system, 
- no firewall had been added or activated. 
- My router is configured to forward 6881 port to my computer. 
- I am using static IP address. 

Any advice? Thanks a lot! 

cheok

---

### Post by yccheok on 2005-05-30
[QUOTE=yccheok]Hi, I had faced this problem for several days. Previously, my router was configured to use Azureus with no problem. 

After I upgraded to latest ubuntu 5.04 and latest Azureus 2.3.0.2, I experience some problem. I have 4 torrents running, all of them are showing green face. However, even I let them run overnight, no single byte was downloaded. 

When I perform NAT test on port 6881, sometimes I will get OK result, sometimes I will get error result. 

I check my ubuntu system, 
- no firewall had been added or activated. 
- My router is configured to forward 6881 port to my computer. 
- I am using static IP address. 

Any advice? Thanks a lot! 

cheok[/QUOTE]
 What is more cocern me is that I can see the new exception thrown in 2.3.02 which I had not seen in prev version
[8:34:51]  NAT tester using central routing for server socket
[8:36:57]  PRUDPPacketHandler: send failed - java.lang.NullPointerException
	at java.net.DatagramSocket.send(DatagramSocket.java:588)
	at com.aelitis.net.udp.impl.PRUDPPacketHandlerImpl$4.runSupport(PRUDPPacketHandlerImpl.java:693)
	at org.gudy.azureus2.core3.util.AEThread.run(AEThread.java:54)

[8:37:46]  NAT tester using central routing for server socket
[8:38:25]  NAT CHECK FAILED: Can't connecto to 218.111.158.106 on 6881
[8:38:58]  NAT tester using central routing for server socket
[8:39:06]  PRUDPPacketHandler: send failed - java.lang.NullPointerException
	at java.net.DatagramSocket.send(DatagramSocket.java:588)
	at com.aelitis.net.udp.impl.PRUDPPacketHandlerImpl$4.runSupport(PRUDPPacketHandlerImpl.java:693)
	at org.gudy.azureus2.core3.util.AEThread.run(AEThread.java:54)

[8:39:44]  Incoming connection from [R: 213.186.46.164: 45040] successfully routed to NAT CHECKER

I get this error message when I try to test on NAT. I tested for 3 times and I get ok at the third time.

---

### Post by yccheok on 2005-05-31
hello, I able to solve this problem by siwtch back to azureus-2.2.0.2 and j2sdk1.4.8.

---

