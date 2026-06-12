---
title: "USB Saitek Flight Yoke works perfectly for 5 minutes then freezes"
date: 2013-04-19
forum: Gaming &amp; Leisure
---

### Post by mrc01 on 2013-04-19
Subject says it all. Using Flightgear. Ubuntu 12.10 32-bit on dual core 3.2 GHz with 4 GB RAM.

At first:
lsusb showed the Yoke and pedals
command line tools like js_test and calibrate worked
Flightgear instantly recognized them and worked
A few seconds into the flight, the controls stopped working
(the yoke and throttles stopped working but the pedals still worked)
even after they stopped working, they still showed up under 'lsusb'
Flightgear would show an error message in the console, something like "/dev/input/js0: no such file"
when they stopped working in FlightGear, they also stopped working in js_test and other cmdline utilities
(these utils would see the controls but no movement would register)

What I did:
created a rules.d file to open the permissions on the device files
this worked: perms on /dev/input/js0 and /dev/input/js1 went from 644 to 666
plugged the yoke in first, then the pedals, to ensure yoke was js0 and pedals were js1
this worked: yoke became js0 and pedals became js1

What happened next:
Flightgear works perfectly for about 5 minutes
About 5 minutes into the flight, the yoke and throttles suddenly stop responding
Pedals (separate USB connection) still work
Even after the controls stop working, the "/dev/input/js0" error message never appears anymore

What I did:
Pause the simulator, unplug the yoke from the USB, plug it back in
Sometimes, it starts working again and I can resume flight

In short, it works perfectly then freezes after 5 minutes. Help!

---

### Post by mrc01 on 2013-04-20
More info:
Symptoms were consistent with USB going into auto-suspend mode, so I checked my system and USB was set to autosuspend after 2 seconds. I added "usbcore.autosuspend=-1" to my kernel boot, confirmed this was set after boot.
This fixed some intermittent USB problems this machine was having, but the yoke & throttles still froze/hung after a few seconds to a few minutes.

No solution to this problem, I am returning these yoke/pedals as defective.
BTW, this is a dual boot box and the same problem occurred in Windows too.

---

