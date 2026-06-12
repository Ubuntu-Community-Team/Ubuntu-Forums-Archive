---
title: "bandwidth monitor?"
date: 2006-01-16
forum: Desktop Environments
---

### Post by Maelgwyn on 2006-01-16
Hi guys,
 
I'm changing ISP's soon to one that gives me basically an unlimited amount of bandwidth (at a price though!)...
 
What I'm looking for is something that I can install on my computer and my flatmates (all Windows... *spit*) to monitor everyone's bandwidth..
 
OR if possible, a snooper of some kind to tell me the bandwidth used for each IP (and I'd need to then setup an IP for everybody's PC!).
 
Is this possible??

---

### Post by awi on 2006-01-25
What is your default gateway? a linux box? a unix box? a router?
For the full usage, you could use MRTG.
For individuals, it depends on your configuration.
One choice is to use iptables in combination with rrdtool, and have some graphics like this:

[http://www.linux.org.py/rrdtool/eth0_py.html](http://www.linux.org.py/rrdtool/eth0_py.html)


But it all depends on your configuration and on your base software.

---

