---
title: "SMC wireless USB dongle"
date: 2008-12-21
forum: General Help
---

### Post by porchrat on 2008-12-21
OK I'm going to attempt to get a wireless USB dongle running on 32bit Hardy system (I know what you're all thinking and yes I'm shuddering too).

I realise these USB dongles can be quite tempermental, is there anyone who has any particular experience with this model of SMC dongle (I don't remember the exact product code, but I think it is something like SMCWUSBT-G), it is a 802.11b/g device and from what I have read I believe it is using the Atheros AR5523 chipset.

From what I have read it seems that people in the past (keep in mind that this dongle is old) have used ndiswrapper.  Some even say that Ubuntu comes with native drivers for the thing (I doubt it, but who knows).

What I want to know is has anyone had any direct experience with this particular product and if so could you direct me to a guide or something? ...or am I overthinking this one?

---

### Post by geraldm on 2008-12-21
The model cited uses driver zd1211rw.
USB VendorID=083a
USB ProductID=4505
If this is the model that you have, this driver should be in hardy.
When posting, get the exact model that you have.

Gerald

---

### Post by porchrat on 2008-12-22
> **geraldm said:**
> The model cited uses driver zd1211rw.
USB VendorID=083a
USB ProductID=4505
If this is the model that you have, this driver should be in hardy.
When posting, get the exact model that you have.

Gerald

Sorry about that I meant to come back and make sure about that, but it was actually a friend's machine and I didn't have the device in front of me at the time.  Still you are right and I will try to have the model number handy next time.

Anyway I double checked and the model number is actually "SMCWUSBT-G2" so I was only off by the last digit.  Where exactly did you find the information on that driver? and is it still pertinent to this device?

I plugged the darn thing in and got no response whatsoever, I couldn't make out anything of value in 'dmesg' either.

Tried ndiswrapper and it seems to work well enough, but the drivers are dropped once a restart is performed (even if I add the ndiswrapper to /etc/modules).

---

### Post by geraldm on 2008-12-22
information was from [http://www.linuxwireless.org/en/users/Devices/USB](http://www.linuxwireless.org/en/users/Devices/USB)

the newer model is based on an aetheros chipset. Manufacturer's site:
[http://www.smc.com/index.cfm?event=viewProduct&localeCode=EN_USA&cid=5&scid=31&pid=1599](http://www.smc.com/index.cfm?event=viewProduct&localeCode=EN_USA&cid=5&scid=31&pid=1599)

You might look into working with ndiswrapper.  Some users have found a way to
get drivers loaded on boot with the wrapper.
Good luck,

Gerald

---

