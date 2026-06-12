---
title: "Ubuntu (8.04), Freezes up."
date: 2009-05-10
forum: General Help
---

### Post by LewisBlah on 2009-05-10
After about a 2 years of toying with the idea I finally switched to Ubuntu, and I could not be more impressed having switched from windows.

I have not hit many problems with hardy that I have not been able to overcome from simply using a Google search. However, for this I have read about similar problems but have yet to come across an answer to what the problem actually is or a solution.

Basically, at seemingly random intervals Ubutnu just freezes, the screen is locked the currsor will not move and all the lights on my keyboard flash (Caps, ScrlLK and Num). I have tried waiting for the computer to  responsive, but the only way is to reboot.

As best as I can tell, the cause could be absolutely anything. Some days I have used the OS all day lets say shut down after 8 hours running and the problem has not occurred. Yet others I have booted up and within 5 minutes (possible less) and it just freezes up. 

Could someone please point me in the right direction. :)

Is this the right place on the forum to post?
Do I need to give any details on the spec of my computer?

---

### Post by Melk79 on 2009-05-10
What you're describing sounds like a kernel panic.  Yes, please post the details on your computer and what exactly is occurring, i.e. you're on Firefox and out of nowhere it locks up or are you doing something else, or nothing at all.  I seem to remember laptops with Intel wireless chips having this issue occasionally.

---

### Post by LewisBlah on 2009-05-10
> **Melk79 said:**
> What you're describing sounds like a kernel panic.  Yes, please post the details on your computer and what exactly is occurring, i.e. you're on Firefox and out of nowhere it locks up or are you doing something else, or nothing at all.  I seem to remember laptops with Intel wireless chips having this issue occasionally.

Thanks for the quick reply! 
Its an old custom made computer which I have added to and upgraded over the years.

**Specifications:**
AMD Sempron Processor 3000+
1GB ram (reads as 1011 MB in system monitor)
Nvidia fx5200 graphics card (Or something similar)
Edimax Wireless lan PCI 'IEEE 802.11g' Network Card

*if any other specifications are needed I can retrieve them*

As for what I'm doing when the lock up occurs, I know the last time it happened I was watching a flash video in 'Firefox 3', while attempting to sync my iPod in 'Amarok'. As for the previous times this has happened I can't recall what programs were running. I have been 6 hours and more today without a freeze up. :)

---

### Post by Melk79 on 2009-05-10
Make sure your system is up to date through Update Manager if you haven't already.  If it happens again, try this key [combo]("http://en.wikipedia.org/wiki/Magic_SysRq_key") to recover and see if there is any pattern leading to the panics.  You can look in you system logs (under System>Administration) to see what messages were occurring just before the panic to try and pinpoint the cause.

---

