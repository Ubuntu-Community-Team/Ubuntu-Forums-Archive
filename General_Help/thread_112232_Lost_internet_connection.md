---
title: "Lost internet connection"
date: 2006-01-03
forum: General Help
---

### Post by swregulator on 2006-01-03
Gang,

I have a dual boot system with Linux on a separate drive and the boot controlled by grub.  When I boot Linux and connect to the internet, the internet connection is randomly terminated.  To get back on, I typically need to boot XP and repair the internet connection, sometimes twice.  When I do so, I can then reboot ubuntu and once again connect to the internet.  Then sometime later I may be disconnected again, go through the same process, etc.

Any thoughts?

---

### Post by darth_vector on 2006-01-03
what type of connection is it? are you on a lan, and sharing the connection? are you connecting through a router? do you use DHCP or a static IP?

we need a little more information :)

---

### Post by swregulator on 2006-01-04
Darth,

Its an ethernet connected to a router connected to a cable modem.  The router also connects two other computers.  The connection to the router is a cable, not wireless.  It is DHCP.

---

### Post by sharke on 2006-01-04
it sounds like a dns problem try setting the dns manually but leave dhcp auto.
regards
Sharke

---

### Post by Randux on 2006-02-01
Sounds like everybody with a cable modem is having problems???

---

### Post by barryp3uk on 2006-02-02
Hi

I had a problem like this. Read my thread at

[http://www.ubuntuforums.org/showthread.php?t=121435](http://www.ubuntuforums.org/showthread.php?t=121435)

I discovered that my error was in not switching off my router between sessions. It was losing its settings when it had been on too long & inactive.  I found it easier, due perhaps to my inexperience to fix that in XP pro (I think XP is quite good at picking up situations like that) & then Ubuntu would be Ok again.

Maybe something simple like this will help.

Best wishes!

Barry.

---

