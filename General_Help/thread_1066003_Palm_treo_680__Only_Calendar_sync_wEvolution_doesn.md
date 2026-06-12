---
title: "Palm treo 680 : Only Calendar sync w/Evolution doesn't work - no errors"
date: 2009-02-10
forum: General Help
---

### Post by bonzgirl on 2009-02-10
Hi,

 I have Treo 680 (w/o data plan), and trying sync Palm - Evolution via Gnome Pilot.

 After fresh install of Evolution, I tested hotsync. It worked fine, and it did sync all the calendar events to Evolution.  

 After I confirmed sync works, I deleted all the events, created two calendars in Evolution, and have imported most updated ical to Evolution (my original events in treo was a bit out dated).

 Now, I'm trying to sync these data w/Palm, and this is where the problem starts.  It looks like hotsync button starts sync smoothly, and show no error.  Contacts sync seems to be working fine, however any of Calendar events or Memo are not syncing. 

 I'm pretty new to Ubuntu. Any logs I can look up to find out detail sync log?  The log on Palm device shows no error, and dont' have much info anyway...

 Or is this because I created two calendars in Evolutions?  My treo has same set of calendar name already...  I thought it will sync fine, but no luck so far...

 I would appreciate any tips/advices!!
 
-bonzgirl

---

### Post by bonzgirl on 2009-02-11
After googling all day, I almost gave up, but tried to rename ~/.gnome2/gnome-pilot.d (or delete), and start gpilot applet again. It did work!

I haven't tested memo and todo yet, but it seems calendar started syncing fine as well as Addressbook/contacts (addressbook sync was working before tho).

-bonzgirl

---

