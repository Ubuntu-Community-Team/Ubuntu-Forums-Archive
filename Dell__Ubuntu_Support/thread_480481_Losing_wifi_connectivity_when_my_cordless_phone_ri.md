---
title: "Losing wifi connectivity when my cordless phone rings"
date: 2007-06-21
forum: Dell  Ubuntu Support
---

### Post by Chasoid on 2007-06-21
Whenever my cordless phone rings, my new Dell E1505N is disconnected from its wireless (802.11G) connection to my router.  The strange thing is that this **ONLY** happens to my Dell E1505N running Feisty.  There are five other laptops in the house (two of them other Dell models) that are also running 802.11G and are completely unaffected when the phone rings.

When the phone stops ringing, or is answered, the connection is automatically re-established.  I don't get dropped from anything (like SSH), but I can't do anything across the wifi network while it's not connected (duh!).

The problem only happens when the phone is actually ringing -- i.e., not when I'm just talking on the phone, dialing a number, or anything else.

What gives?  Is 802.11G living on the same frequency with my phone's ringer?  That would by annoying, yet kind of funny.  :)

Thanks!

---

### Post by sagarhshah on 2007-06-21
you could try chaging the ringer in the phone althought that would involve opening it up etc and probably voiding your warranty for your phone.

---

### Post by Chasoid on 2007-06-21
I don't think it's the actual ringer in the phone that's causing the problem.  I've tried placing the laptop far away from the phone's "base station", but unless I get far away -- like across the street ... roughly 100 feet -- the phone ringing knocks out the wifi.

Thanks just the same!  :D

---

### Post by timcredible on 2007-06-21
your phone is running on the same frequency as 802.11b and 802.11g, namely 2.4Ghz.  802.11a runs in the 5.8Ghz range.  There's only a few unlicensed frequencies available for things like cordless phones and networking: 900Mhz, 2.4 Ghz, 5.8Ghz, so everything unlicensed, including microwaves, run in one of those frequencies.  Sounds like your cordless phone's 'theres a call' message between the base and the handset is being misinterpreted by your wireless card and/or drivers as something else and the connection drops.  the easy solution is to buy a cordless phone that runs at 5.8Ghz.

---

### Post by Seq on 2007-06-21
I used to have a similar problem. I believe my issue was resolved by either changing the channel on the handset, or by changing the channel on my WAP.

I did a site survey, and apparently everybody leaves it on the default channel 6 (including myself until then), so I actually seem to get better wifi reception now too. YMMV.

---

### Post by TurboPotato on 2007-06-22
Change the channel on your Router or Access Point to something non-standard.  Try channel 1 or Channel 11 these trend to be channels that usually aren't used as heavly.

Is your laptop close to your cordless phone base?  Or a microwave?  Move the Access Point as far away from these things as possible.

---

### Post by Tethtibis on 2007-06-26
it might be the channel it is using, try going into your router, and disabling the channel the affected comp is using.

---

