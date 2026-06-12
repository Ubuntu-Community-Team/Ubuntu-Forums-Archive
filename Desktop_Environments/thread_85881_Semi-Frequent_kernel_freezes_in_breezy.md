---
title: "Semi-Frequent kernel freezes in breezy?"
date: 2005-11-03
forum: Desktop Environments
---

### Post by kreso on 2005-11-03
Almost once a day my ubuntu freezes, on both my laptop and desktop pc. Sometimes it's the screensaver, sometimes its the usb stick etc etc... Has anyone else experieced this?

I ran hoary for 4 months and I never experienced a single kernel freeze!

---

### Post by mwillems on 2005-11-03
Same here exactly. Once a day it freezes, in screensaver or some other random act. After it freezes there is NOTHING More logged in /var/log/messages, until I hard reboot.

This is a total showstopper unfortunately, so I hope the many occorances of this are solved soon.. by someone... ;)

---

### Post by kreso on 2005-11-05
How can I (easily) install the new 2.6.14 kernel?

---

### Post by spizkapa on 2005-11-05
[QUOTE=kreso]Almost once a day my ubuntu freezes, on both my laptop and desktop pc. Sometimes it's the screensaver, sometimes its the usb stick etc etc... Has anyone else experieced this?

I ran hoary for 4 months and I never experienced a single kernel freeze![/QUOTE]

I suspect your problem is with power management and apm/acpi. Turn off power management from the advanced screensaver options and see if that helps. Try to avoid using opengl screensavers, I have found that they tend to freeze systems when power management is on. Most laptops have really crappy power management hardware and without specs, it's a stab in the dark to get them to work.

Also, install the right kernel for your processor, that's likely to help. Of course, if you're running the proprietary drivers for nvidia or ati, they may have something to do with the lock ups too.

---

### Post by mwillems on 2005-11-05
I'll turn off power management, though that would be a sowstopper (I don't want my screen backlight to be on at all times). I use whatever drivers Ubuntu installs for my card: how would I Know? It's an ATI Radeon 9100.

---

