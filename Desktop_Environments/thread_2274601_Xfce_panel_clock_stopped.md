---
title: "Xfce panel clock stopped"
date: 2015-04-21
forum: Desktop Environments
---

### Post by zablankinship on 2015-04-21
Just noticed this little bug. Anyone else have problems with the xfce clock?

**Problem: **Default XFCE 4.10 clock panel add-on freezes upon boot-up in Xubuntu 14.04.2.
**Workaround: **
Use Orage clock instead:
```
sudo apt-get install orage
```
Add Orage clock to panel, remove default clock.

[ATTACH=CONFIG]261447[/ATTACH]

---

### Post by kerry_s on 2015-04-21
lol, it's cause it's lunch time, 1 hour & it'll work again.

---

### Post by Adam_GUI on 2015-04-21
I had a similar issue a while back where xfce pinged a time server for the current hour, but would use my motherboard CMOS clock  for the minute value.  My motherboard was fifteen minutes faster than any other clock I had.

Changed the time in the BIOS and things went back to normal for me.

---

### Post by matt_symes on 2015-04-21
Hi

Does running ntpdate manually fix the problem ?

```
sudo ntpdate {0,1,2,3}.ubuntu.pool.ntp.org && date
```

Kind regards

---

### Post by zablankinship on 2015-04-21
Output for: 
```
sudo ntpdate {0,1,2,3}.ubuntu.pool.ntp.org && date
```
is as follows:
```
21 Apr 10:55:58 ntpdate[2504]: adjust time server 129.6.15.30 offset -0.181174 sec
Tue Apr 21 10:55:58 EDT 2015
```

Looking in the Date & Time properties, it seems like the clock starts at boot up, but then freezes up. According to my system settings, it knows what the correct time is, its just that the panel clock does not recognize it. If I remove the clock from the panel, re-add it back on, it updates to current time. Strange that is. Heres a shot of my settings...
*Note: when I opened up the clock settings, the clock panel time jumped ahead about 4 minutes ahead of actual time, and now it is once again frozen. Can't make it happy 
[ATTACH=CONFIG]261448[/ATTACH]

---

### Post by matt_symes on 2015-04-21
Hi

I'm not sure what the reason why your panel clock is not working however i use the orage clock that also contains a calendar.

If you install the orage clock and add that to your xfce-panel, do you still get the same issue ?

```
sudo apt-get install orage
```

Add to the panel like any other applet.

You may have to restart the panel to show the clock (i can never remember).

```
xfce4-panel --restart
```

Does the orage clock work for you ?

Kind regards

---

### Post by zablankinship on 2015-04-21
Yes, I have Orage installed and that clock works just fine. So it seems the problem lies in the default clock add-on. By the way, a panel restart does not fix the default panel clock, so still not sure what's going on with that. But I may just end up using Orage from now on anyway.

I have installed Xubuntu 14.04 many times and this is the first I've seen of this, so its more of a freak glitch than anything else.

---

### Post by matt_symes on 2015-04-21
Hi

> **zablankinship said:**
> Yes, I have Orage installed and that clock works just fine. So it seems the problem lies in the default clock add-on. By the way, a panel restart does not fix the default panel clock, so still not sure what's going on with that. But I may just end up using Orage from now on anyway.

I have installed Xubuntu 14.04 many times and this is the first I've seen of this, so its more of a freak glitch than anything else.

It's a weird one alright and without further digging I, for one, am clueless to the reason why :)

If your happy using orage though, further investigation is mute and probably not the most beneficial use of both our time.

You may want to mark this thread as [SOLVED] but i'll leave that decision up to you as it's more of a work around.

Kind regards

---

