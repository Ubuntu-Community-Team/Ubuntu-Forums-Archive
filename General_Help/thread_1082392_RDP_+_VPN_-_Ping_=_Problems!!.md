---
title: "RDP + VPN - Ping = Problems!!"
date: 2009-02-27
forum: General Help
---

### Post by nisarg on 2009-02-27
Chaps & Chappies,

I have shed a lot of sweat searching the web and forums here but no joy; atleast couldnt find anything related.
I am running 8.10, and I need to get onto to one my Windows 2003 box at work over the VPN. The VPN we use at work is a Windows native PPTP. So I installed the PPTP plugin for network manager, configured - and configured everything....sweet! click, click, over to VPN connections..and select the connection..and boom... nice little animation and a golden lock secured the network-manager icon. I was VPN'ed into my work and now I can even ping the box I need to connect (60% of packets are lost everytime though).
Anyways, I run up the Terminal Server Client from Applications->Internet ...enter the IP, select RDPv5 and Connect..... and window disappears. I can see the process, so I let it take its time; and to my despair, it comes back with an ERROR - Cannot Connect. No idea what's going on here?

Anyone? Any help will be much appreciated.

Cheers,

---

### Post by Tom_T on 2009-02-27
Hi
I VPN in to a Windows 2003 server and run the Terminal Service Client.

I set the VPN up following this:
[http://www.splatdot.com/2008/11/19/ubuntu-810-how-connect-microsoft-vpn](http://www.splatdot.com/2008/11/19/ubuntu-810-how-connect-microsoft-vpn)

Then configured the TSC to use RDP **NOT** RDPv5. 
If I used RDPv5 it would fail.. Using RDP works for me !

Hope that helps :)

---

### Post by nisarg on 2009-02-27
Cheers for the response, matie.
I have tried RDP as well, same issue as with RDPv5 ... none works.
Just a super lame error message - cannot connect!

> **Tom_T said:**
> Hi
I VPN in to a Windows 2003 server and run the Terminal Service Client.

I set the VPN up following this:
[http://www.splatdot.com/2008/11/19/ubuntu-810-how-connect-microsoft-vpn](http://www.splatdot.com/2008/11/19/ubuntu-810-how-connect-microsoft-vpn)

Then configured the TSC to use RDP **NOT** RDPv5. 
If I used RDPv5 it would fail.. Using RDP works for me !

Hope that helps :)

---

### Post by nisarg on 2009-02-27
HA HA !! 
Looks like its just gave up... 
I am able to get on to the box just fine now. The issue was nothing but the login, it needed the domain name in the VPN config. I entered that and boom.. straight onto the desktop...
How was it connecting it in the first place, and pinging it fine though? anyways - it all works now! 
Thanks everyone who have looked at the thread, and ofcourse the ones replied ;)

Cheers!

---

### Post by nisarg on 2009-02-27
And yeah, mate - it indeed only works with RDP and not with RDPv5!! So your right. Thanks, again.

:guitar:

> **Tom_T said:**
> Hi
I VPN in to a Windows 2003 server and run the Terminal Service Client.

I set the VPN up following this:
[http://www.splatdot.com/2008/11/19/ubuntu-810-how-connect-microsoft-vpn](http://www.splatdot.com/2008/11/19/ubuntu-810-how-connect-microsoft-vpn)

Then configured the TSC to use RDP **NOT** RDPv5. 
If I used RDPv5 it would fail.. Using RDP works for me !

Hope that helps :)

---

