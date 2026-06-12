---
title: "OpenArena can't connect to servers"
date: 2009-02-21
forum: Gaming &amp; Leisure
---

### Post by qbee42 on 2009-02-21
Ubuntu 8.10
OpenArena 0.8.1-2

Firestarter firewall shows no outbound controls.

The computer in question is behind a NAT router, but the same problem exists if I connect directly to the cable modem without the router. Furthermore, OpenArena runs normally on two other computers behind the same NAT router.

My OpenArena was working fine, but now I can no longer connect to servers, whether Internet or local. The server browser populates correctly with a list of servers, but when I select one OpenArena stays at the "AWAITING GAME STATE" screen. OpenArena is still responsive at this point: I can back out of the screen, go back to the server browser, or play a stand-alone game.

Looking at the console shows this error message relating to the IP of the selected server:

"Sys_StringToSocketaddr: Error resolving : No address associated with hostname"

The hostname is the IP address of the server.

After that the console shows a Shutdown(0) and normal restart.

Doing a network sniff shows two interesting lines repeating:

66.246.138.193	192.168.0.40	QUAKE3	Game Client to Server

192.168.0.40	66.246.138.193	ICMP	Destination unreachable (Port unreachable)

Where 192.168.0.40 is the game computer, and 66.246.138.193 is the OpenArena server on the Internet.

Any ideas would be greatly appreciated.

Thanks,
Tom

---

### Post by qbee42 on 2009-02-22
More information: I ran a network protocol analyzer and took a good look at the activity. The ports are working fine. Comparing the problem machine to one working okay, everything progresses the same up until the problem machine shows this error on the console:

"Sys_StringToSocketaddr: Error resolving : No address associated with hostname"

For some reason it can't resolve a simple IP address to the same IP address. It shows that error message, the on the next line states that the address has been resolved to the same address, then it just sits there.

Looking at the network trace, I can see that all of the communication between my computer and the server has been fine to this point. The server and client are exchanging game state information. When everything stops in the console, the network trace shows that the local port has been closed. After a couple of tries the server gives up.

So it looks to me like my installation of OpenArena is hanging up on that error, at least from a multi-player perspective. Hitting escape works to bring me back to the main menu.

I have tried removing OpenArena and re-installing, but the problem is still here. Perhaps I am not getting everything removed, or perhaps there is some other conflict.

Any ideas?

Tom

---

