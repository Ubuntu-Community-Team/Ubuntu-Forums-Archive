---
title: "Ethernet not working"
date: 2012-08-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Xavier1 on 2012-08-12
I will try to narrow down my problem to the first thing that seems to go wrong:

On ubuntu 12.04, the ethernet connection does not work. I am told that it is disconnected. Any idea as to why that might be? Bear in mind that wireless doesn't work either.

Using a Dell Inspiron 1720

---

### Post by 2F4U on 2012-08-13
Some things that come to my mind. These are just guesses since you provide almost no valueable information.
- Network adapter is damaged
- Network cable is broken/damaged
- Connection between cable and network outlet is loose or not properly connected
- MAC address blocked in router
- IP addresses depleted so that DHCP server does not assign addresses
- Wireless adapter requires special driver not provided by Ubuntu

---

### Post by Tobeus on 2012-08-13
1. check your bios settings to make sure your on board networking is enabled.  (f2 to enter Dell bios at Dell boot screen).
2. Try a different network cable.
3. Check to see if the lights are lit on the network port (assuming you are talking about the on board Dell port).
4. Are they lit on the router/switch?  If no lights show up, could be a bad port on the computer, or on the switch/router, or even a bad cable (see 2).

If you are actually seeing a "Disconnected" error, then the problem is hardware-related, not Ubuntu related.  I could be wrong, but usually that's what I find.

Do you have a dual boot system?  If you do, see if the wired connection works in the other OS.

That's about all I have to throw to ya.  Good luck, and hope this helps!

-Tobeus

Oh yeah, and check inside the ports of both the system and the router/switch to see if any green corrosion is on the contacts.  Sometimes moisture gets into those ports some how (humid, moist environment, spill, etc.) that corrodes the contacts.  If you see green, try reinserting the network cable over and over while the computer is turned off.  After about 20 reinsertions it should start to work if the corrosion didn't damage anything permanently.  If there's green and reinsertions don't help, go buy a network card or usb network adapter to install.

---

### Post by Tobeus on 2012-08-13
Also, it's not nice to start a new topic/thread when you already have one started on this issue.  

[INDENT][http://ubuntuforums.org/showthread.php?t=2040268](http://ubuntuforums.org/showthread.php?t=2040268)
[/INDENT]Your other thread has more info that can be helpful for troubleshooting anyway, such as the connection works in Vista.

That is what you are talking about here too, right?

-Tobeus

---

