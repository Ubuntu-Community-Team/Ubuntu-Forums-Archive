---
title: "Bus Error with Transmission"
date: 2009-05-15
forum: General Help
---

### Post by himynameisdaniel on 2009-05-15
Hi guys, what exactly is a bus error?

The problem I'm getting is that transmission worked fine, I was playing around with the blacklists. Next time I opened it (might not have shut it down properly?) it wouldn't open, so I tried opening it with the terminal and it just says "bus error". 

I have tried complete removal in synoptic, restarted and then installed again but no luck with that.

Any other suggestions?

---

### Post by lovinglinux on 2009-05-15
I don't know what dbus error is, but you could try deleting the content of ~/.config/transmission/blocklists/

---

### Post by himynameisdaniel on 2009-05-16
Complete removal automatically erases all the configuration settings does it not?

Can anyone enlighten me as to what a "bus error" exactly is and then it might be solvable from that :popcorn:

---

### Post by kamikazejoe on 2009-05-30
I don't know what the error exactly is or what is causing it, but I think I've discovered a workaround.  If you start Transmission from the terminal like so:

[FONT="Courier New"]kamikazejoe@bettie:~$ transmission -p[/FONT]

It will start with all your pending torrents paused.  Then you can start them manually.  At least until the problem is fixed.

---

### Post by godbhaal on 2013-01-25
> **lovinglinux said:**
> I don't know what dbus error is, but you could try deleting the content of ~/.config/transmission/blocklists/

It works!

---

### Post by oldos2er on 2013-01-25
Old thread closed, please don't bump old threads.

---

