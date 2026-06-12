---
title: "How to connect to remote IPP printer???"
date: 2006-03-16
forum: Desktop Environments
---

### Post by pointym5 on 2006-03-16
I've got two Ubuntu machines (one Hoary still, one Breezy).  The Hoary machine has a printer, and in the past I've been able to print to it over the network.

When I went from Hoary -> Breezy on the other machine, I lost all the printer configuration stuff (the upgrade was disastrous failure and I had to reinstall). Now I cannot get the Breezy machine to connect again.  I go through CUPS but am given no clues whatsoever as to why the URIs I've tried do not work. From the Hoary machine (i.e., the machine with the printer), I cannot find any way to get it to tell me what the external URI for its shared printer is (which is, in my opinion, an incredible omission of functionality).

How in the world is this supposed to work, and why is the mechanism so coldly unhelpful?

---

### Post by kiwigander on 2006-03-19
I agree, CUPS is a lot less user-friendly than its slick appearance would suggest.

I've run into this problem repeatedly, having several times changed the distribution installed on my wife's PC; she's got the colour printer.  I'm not a skilled user, so no guarantees here, but here goes:

1. Let's assume that your Hoary machine with the printer directly connected is at 192.168.x.a and your Breezy machine is at 192.168.x.b.

2. On the Hoary machine, find out (using System > Administration > Printing) what the printer is called.  No need to worry about what port it's connected to, just its name.  For example, say it's called LaserJet_Series_2.  

3. On your Breezy machine, use System > Administration > Printing to delete any reference to the printer, and then set up a new printer.  Printer Type will be Network Printer and the sub-type CUPS Printer (IPP).  

4. The slightly tricky part is the URL, which will be

[http://192.168.x.a:631/printers/LaserJet_Series_2](http://192.168.x.a:631/printers/LaserJet_Series_2)

that is, the URL is an http:// address even though the protocol is IPP.

Sorry if this doesn't work and especially if I've insulted your intelligence.  I just find, if I make instructions simple and unambiguous enough that I can't go wrong with them, then they usually work for everyone else.  :)

---

