---
title: "Dell Mini 9 won't stay connected to internet"
date: 2008-12-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by thomaston on 2008-12-31
I'm a new user to Linux with this Mini 9. It's been working great until a couple of days ago when my wireless would start dropping the signal after a couple of minutes. I re-start, it re-connects, and then drops the signal all over again after a couple of minutes. The icon that shows the connection will go from 4 bars to zero bars.
I've searched and searched for a solution, but all I've found are people having problems connecting in the first place.
Oh yeah, this is happening on 2 different wireless networks, and I've already tested those side-by-side with another computer to make sure it wasn't a network problem.
I just ran the update manager during one of my brief periods of connectivity to make sure everything is up to date.
Help, please? Like I said, I'm new at all this, never used the terminal, and frankly find a lot of what I've read here so far to be gibberish. So I'll need "directions for dummies" most likely.

PS- this is the standard Dell version of 8.04 with the hardware they use. Everything is still in the same configuration as it was out of the box.

---

### Post by armandh on 2008-12-31
mine has been rock solid from the basement to the 2nd floor.

were I to guess 

make sure the battery connection is good
suspect battery
does it do it with the charger plugged in? 

if not battery then thermal issues 
is the mini 9 on a hard cool surface with the air vents not obstructed. 

if a fan aimed at the vents delays the process the wlan card may be bad.

---

### Post by thomaston on 2008-12-31
I just tried it while plugged in. It did stay connected a minute or two longer than it usually does, but then it dropped the connection again.
As far as the heating issue, the problem is happening even when the computer has been turned off for several hours.
I'm worried this will end up being a hardware issue that can't be fixed without returning it.

---

### Post by thomaston on 2008-12-31
Ok, maybe it's a heating issue after all. I let it cool down for a while, and then turned it on and placed it in my lap in such a way that the bottom wasn't touching me. It worked fine for 10-15 minutes. As soon as placed it on a level surface that covered those bottom vents, my connection went to 0% again.
Either it's a coincidence, or that bottom panel can't handle being covered at all.

---

### Post by magicfab on 2008-12-31
Look at the logs in System > Administration > System log, in "syslog", you may see an indication of what's wrong.

---

### Post by thomaston on 2008-12-31
Here's what I'm getting under syslog:
NetworkManager: <WARN> nm_device_802_11_wireless_set_essid(): error setting ESSID to 'PUBLIC'for device ethl: Invalid argument

NetworkManager: <WARN> nm_device_802_11_wireless_set_wep_enc_key(): error setting key for device ethl: Invalid argument

NetworkManager: <WARN> request_and_convert_scan_results(): unknown error, or the card returned too much scan info: Invalid argument

I'm getting the last one over and over, even when the computer is just sitting there.

---

### Post by JRSinOK on 2009-01-03
Not that this is any help, but I am having the exact same issue with the same mini 9.  Like you i am new to ubuntu and not sure what to do!

I get a similar message right before it cuts off the wireless

Jan  3 16:44:38 jimmy NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 

Can someone tell me what this means and how to fix???

---

### Post by armandh on 2009-01-03
sounds like a thermally intermittent wireless card
time to call dell

---

### Post by thomaston on 2009-01-23
I just said this in JRSinOK's thread by mistake, but I sent mine off to Dell thinking my wireless card was bad. Got it back today to find all they did was re-install the OS. But, it's been working fine now for several hours, so apparently it was a software issue after all.

---

### Post by thomaston on 2009-01-26
Another update... Not long after my last post, my wireless connection went out again, and has been out ever since. I'll be sending it back to Dell for good this time, since they obviously didn't try to diagnose the problem correctly, despite me telling them my wireless card seemed to be bad.

---

### Post by Talon2 on 2009-01-26
> **thomaston said:**
> I just tried it while plugged in. It did stay connected a minute or two longer than it usually does, but then it dropped the connection again.
As far as the heating issue, the problem is happening even when the computer has been turned off for several hours.
I'm worried this will end up being a hardware issue that can't be fixed without returning it.

It could be a hardware issue but I'll suggest this:

If your wireless AP/router is capable of Super G or N, is it possible for you to turn these capabilities off so that the signal is basic 802.11g?  Alternatively, if you have a friend who has a basic 802.11g AP/router you could test with it.

The reason I mention this is that my Mini does great with basic G but sometimes I see problems with Super G.  I have 2 AP's in the house.  One is basic G and one is Super G.

I tend to blame the Broadcom wifi in the Mini.  I really wish Dell had used Intel wifi kit.

---

