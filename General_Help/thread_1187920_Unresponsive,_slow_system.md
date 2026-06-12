---
title: "Unresponsive, slow system"
date: 2009-06-15
forum: General Help
---

### Post by blazemore on 2009-06-15
I'm running an almost vanilla Jaunty Netbook Remix on an Acer Aspire One, the one with an 8gb SSD.

It is SO SLOW and unresponsive. When I alt+tab, it will be maybe 5-10 seconds before anything happs.
When I'm typing, sometimes it will just stop, and then all the rest of my typing (while it was stopped) will appear at once.
When I click checkboxes in Firefox, it sometimes takes a few seconds to actually do it.
When I scroll with my mouse wheel, sometimes nothing happens for a few seconds, then it scrolls down the bottom very quickly.

I've tried reinstalling, (that's why it's almost vanilla) and I've even tried compiling my own kernel with the config file on [www.aspireonekernel.com](www.aspireonekernel.com). I've tried using hardware-specific distros such as Linux4One (Too old) and Kuki.me, but the same issues appear in these.

Interestingly, my girlfriend has an Aspire One, but with the 120gb hard disk. It runs very fast on this, so it might be an SSD issue.

I have a 512mb swap partition (as I have 512mb RAM) but I hardly use it since Ubuntu uses only about 200-250mb, so it never needs to swap. I have tried everything, all the guides about optimising for SSD performance and everything. I've tried with ext2, ext3 and currently ext4 (with and without journaling). I've even tried ReiserFS!

Does anyone have any idea how to make the system more responsive? I've disabled all unneccesary things I don't use (Bluetooth etc)

EDIT: Screenshot attatched - Screens like this are all too common on my system...

---

### Post by Soul-Sing on 2009-06-15
Did you run ```
top
``` or ```
htop
```, to see if their are processen going wild.

---

### Post by 987poiuytrewq on 2009-06-15
Not sure if this is the issue but I'm running ubuntu on a Compaq CQ60 and the vanilla install was extremely sluggish until I sorted out the graphics drivers. I think it was using the CPU to render graphics or something? I'm not sure what graphics card you have on the Aspire One, but a look at the restricted drivers list or downgrading to an older driver might sort you out.

---

### Post by blazemore on 2009-06-15
I checked the Processes tab on System Monitor. Nothing using excessing CPU, and nothing using more than 30mb RAM (Most smaller processes use only a few KB, Firefox is the main memory hog at 27.9)

And FYI Compiz is disabled

---

### Post by blazemore on 2009-06-15
> **987poiuytrewq said:**
> Not sure if this is the issue but I'm running ubuntu on a Compaq CQ60 and the vanilla install was extremely sluggish until I sorted out the graphics drivers. I think it was using the CPU to render graphics or something? I'm not sure what graphics card you have on the Aspire One, but a look at the restricted drivers list or downgrading to an older driver might sort you out.

The only restricted driver available is MadWifi. I'm going to try installing linux-restricted-modules or something.

---

### Post by HavocXphere on 2009-06-15
Does a LiveCD do the same thing?

I reckon GFX drivers like 987poiuytrewq said.

Switch off compiz (if its on) and try running with the VESA driver, see if it makes a difference.

---

### Post by blazemore on 2009-06-15
This is really bugging me cos I'm going on a train to London in a couple of hours, and if I'm going to do some evangelism, it needs to be backed up with good, solid performance and stability.

---

### Post by blazemore on 2009-06-15
> **HavocXphere said:**
> Does a LiveCD do the same thing?

I reckon GFX drivers like 987poiuytrewq said.

Switch off compiz (if its on) and try running with the VESA driver, see if it makes a difference.

It's even slower on the LiveUSB
There's no other driver available (Unless anyone knows another way of installing one...?)
Compiz is off, like I said above.

---

### Post by Soul-Sing on 2009-06-15
no zombi processes?

It could be RAM troubles. (Hardware issue's)

---

### Post by blazemore on 2009-06-15
Hmm. Do you think running a memtest would help?

---

### Post by DeMus on 2009-06-15
> **blazemore said:**
> Hmm. Do you think running a memtest would help?

It doesn't hurt. After the test you know if it is your memory or something else. Try it.
I would say it has something to do with your videodriver, seeing more problems here which are caused by it.

---

### Post by blazemore on 2009-06-15
Yes, I'm thinking it might be those infamous Jaunty Intel drivers :P
I'm updating to a new one I found on a PPA, if it works I'll post more detailed instructions here.
I'm also installing SickBoy's kernel from [www.aspireonekernel.com](www.aspireonekernel.com) because the wifi light flashes, and the system boots up faster.

---

