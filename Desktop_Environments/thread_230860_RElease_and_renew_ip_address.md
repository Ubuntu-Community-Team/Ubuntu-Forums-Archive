---
title: "RElease and renew ip address"
date: 2006-08-06
forum: Desktop Environments
---

### Post by Magiczero on 2006-08-06
Hi  How do I release and renew my ip address in Ubuntu bcuz a friend came over and fixed my router and he said I need to release and renew my ip address I know how to on windows but not Ubuntu!!  Can u tell me how to?

---

### Post by stanz on 2006-08-06
Thats a great question ~ I have no answer to. yet.

Check out [my simular thread & results.]("http://www.ubuntuforums.org/showthread.php?t=219748")

Here's [bug info]("http://bugzilla.gnome.org/show_bug.cgi?id=349331") & fellow '[wants to know]("https://launchpad.net/distros/ubuntu/+source/gnome-network/+bug/33447")' folks.

I got my box to release/renew ~ by turning it off, & pulling the power from the back of box,
for 5 or so minutes, then it grabed anew one when turned back on. 
** I Have No Router - So, It's just DSL Modem & PC, & when modem resets IP Addy= PC can't adjust.
I hope this helps, somehow...cause we aren't getting much response on this topic!   :mrgreen:

---

### Post by The Uniphobiac on 2006-08-06
ifconfig eth0 down
ifconfig eth0 up

replace eth0 with your interface

---

### Post by bbzbryce on 2006-08-06
I usually do:
sudo dhclient

It's pretty much exactly release/renew ip as far as I can tell.  Although I have the networking icon on my top taskbar and I can just click on it, and it'll reconfigure it, although I don't know the interworkings of that.

---

### Post by stanz on 2006-08-09
> **bbzbryce said:**
> I usually do: sudo dhclient
It's pretty much exactly release/renew ip as far as I can tell.  Although I have the networking icon on my top taskbar and I can just click on it, and it'll reconfigure it, although I don't know the interworkings of that.
the client gives good output, but I like to know WHERE to go, to manually make changes = to get the fix!?

[quote=The Uniphobiac]     ifconfig eth0 down
ifconfig eth0 up ,  replace eth0 with your interface[/quote]
should we expect any output from these commands or is it working on its own ?
haven't tried it yet with working box..

---

### Post by Cooner750 on 2006-08-09
Wait, if you have a router connected to an internet source (cable modem, DSL Modem), and then the router connected to the computers, shouldn't you be releasing/renewing the WAN IP from the Router, not the computer?

Or is this an issue with the computer not getting an IP from the router?

---

### Post by stanz on 2006-08-12
For me?  It's Pc not getting [and renewing] new IP from DSL Modem

---

