---
title: "Internet won't work when computer's warm"
date: 2006-03-23
forum: Desktop Environments
---

### Post by Twilight Lamentation on 2006-03-23
Hi,

When I first turn my computer on, my internet connection detects just fine and my internet works. However, after rebooting, even if I actually turn the computer off and turn it back on again after a few minutes(I have lockup problems, but that's a whole other issue), the internet won't work; it says something about not being able to find any websites, GAIM can't connect, etc.

It started happening last night, a few days after I installed Ubuntu for the first time. I wandered off for a bit, then turned my computer back on after a few hours and the internet worked. I would have chaulked it up to ISP problems if the exact same thing hadn't happened tonight: when I first turned my computer on after it being off all day, the internet worked fine. Then it locked up, I had to reboot (both just a reboot and an actual power down), and my internet won't work. I haven't gone back to try again, but I'll do that in a bit and let you know what happens.

So it looks to me like, if my computer's warm, my internet connections won't set up properly. Does anyone have any idea what could be going on?

I've got a Dell Inspiron 8200 (yeah I know it's old), and I'm using an Ethernet DHCP connection.

thanks

---

### Post by IYY on 2006-03-23
If this is really happening because of heat, you really need to check the temperature of your machine. It might be way too high; your fan could be broken, or something.

---

### Post by Twilight Lamentation on 2006-03-23
Ok scratch that theory: I just tried after my computer has been off for a few hours (and feels quite cool), and the internet still doesn't work. :(

Edited to add: I'm running the LiveCD right now; I had to manually set up the internet connection (instead of it setting itself up like it did the last few times I used the LiveCD), but now the internet is working.

I did: System --->Administration--->Networking 

then activated my eth0 connection with the exact same settings that I use in my installed version of Ubuntu (DHCP). One thing I noticed was that activating my eth0 connection was much faster running off LiveCD than in my actual installed version. However, the eth0 connection does eventually activate in my installed version (but I can't use the internet).

Any help would be much appreciated!

---

### Post by Twilight Lamentation on 2006-03-23
And here I am, happily surfing the net on my actual installed version of Ubuntu (as opposed to LiveCD), after leaving it off all night.

Does anyone have any idea what could be going on?? I'm so afraid that I'll have to reboot and then my internet will stop working yet again. :confused:

---

### Post by _linux_ on 2006-04-05
Same problem here. I don't know what's wrong! The Internet's okay on Windows, but not on Windows!

---

### Post by Zeroedout on 2006-04-06
[quote=_linux_]Same problem here. I don't know what's wrong! The Internet's okay on Windows, but not on Windows![/quote]

Yes, windows is god, things can work AND not work at the same same time, all hail lord windows, the master of all that is paranormal. On a more serious note though, first thing is what chipset are your NICs using? If you do not know, ```
sudo lshw
``` look for the network info and post the description, product and vender.  this is what mine looks like.
 *-network
             description: Ethernet interface
             product: 3c556 Hurricane CardBus [Cyclone]
             vendor: 3Com Corporation
If you have multiple NICs as I do, further on in the description you'll see it's logical name (i.e. eth0, eth1, wlan0).

---

### Post by jamesr on 2006-04-06
I would suggest as mentioned previously that you check both fans ie PSU fan and especially the CPU fan

---

