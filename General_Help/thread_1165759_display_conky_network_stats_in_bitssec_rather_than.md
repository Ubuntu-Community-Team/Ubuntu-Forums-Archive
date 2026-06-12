---
title: "display conky network stats in bits/sec rather than bytes/sec"
date: 2009-05-21
forum: General Help
---

### Post by RedWagon on 2009-05-21
Does anyone know of a way in conky to display the network speed in bits/sec (like it should be) instead of bytes/sec?  I tried ${downspeed eth0 * 8} just for the hell of it but it didn't work and also googled around a bit but couldn't find anything.  

On a side note, is there some reason that software developers always write their programs to monitor bytes/sec when every single piece of networking hardware measures stuff in bits/sec?  Why do they do it?  Wouldn't it be a lot simpler if everyone just used bits/sec? :mad: This has been bugging me for awhile.

Anyways, if anyone knows how to do this or even a way to manipulate the numbers in the conky config file so I can just * 8 it or even a way to get a clean number from ifconfig or some other command line program so I can do an ${exec ...
thanks!

---

### Post by thedanyes on 2012-01-17
This annoys me too, and still hasn't changed as of 1.8.1

---

### Post by Sector11 on 2012-01-21
> **thedanyes said:**
> This annoys me too, and still hasn't changed as of 1.8.1

**LUA** - talk to mrpeachy or look at his [HOW TO : using lua scripts in conky]("http://crunchbanglinux.org/forums/topic/17246/how-to-using-lua-scripts-in-conky/") - I read where you can multiply results IF you tell LUA to handle output as numbers in there someplace I think.

---

