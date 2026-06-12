---
title: "ubuntu studio 9.1: compiz problem, wireless problem, and advice needed"
date: 2010-10-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by h4x0l2 on 2010-10-12
Hey all

I have all of the effects enabled, cube works (just need to learn how to configure it) and the overall prefomance is impressive considering its running on a 1.6ghz dell inspiron 8200 with 256mb ram. Cpu runs at about 46% like this. When I run just the "neccesary eye candy" it runs at about 23%.

Now, if I were to upgrade from the first release of ustudio9.1 to 10.4, would this help or hurt?

WIRELESS:
My wireless will not connect as well, tried linksys card as well as usb with no luck. It reads my router, sees the ssid, but it won't connect. It asked for password, then cycles and then asks for the password again. Tried wep, wpa, and wpa2. Eth0 works fine.

COMPIZ:
I have no options to increase the number of desktops.. it stays at 1. How do I enable this?

Also, when I use ccsm, what is your configuration reccommendation for making this older laptop seem eye-catching without loss of functionality?

This system will be used for intensive audio production, id like to see how ubuntu works with 256mb ram.

---

### Post by cchhrriiss121212 on 2010-10-13
Intensive audio production on that machine means you should ditch compiz and any network connections. You will need all the system resources you can get.

Even if you weren't using audio I'd recommend removing compiz. You could also look into a lighter desktop environment like lxde or openbox+tint2.

For your wireless try installing wicd.

---

### Post by realzippy on 2010-10-13
In CCSM/General/Desktop Size set slider to 4 to make the cube.

Install *fusion-icon*,so you can simply stop compiz and start metacity
with 1 click when needing all resources for audio production.
Wireless:
Which wlan chip/card are you using?
If no idea,run in terminal
```
lspci
```
and post output.

And:
Welcome to the forum!

---

### Post by h4x0l2 on 2010-11-05
when i start using that machine again, i'll post the specs on it. I retired it for the time being. have a new machine now.

---

