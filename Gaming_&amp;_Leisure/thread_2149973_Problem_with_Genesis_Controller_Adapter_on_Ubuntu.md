---
title: "Problem with Genesis Controller Adapter on Ubuntu"
date: 2013-05-30
forum: Gaming &amp; Leisure
---

### Post by Solid One on 2013-05-30
Hi all.

Recently, I bought [this Genesis Controller Adapter from ebay]("http://www.ebay.com/itm/Sega-Genesis-Controller-to-PC-USB-Adapter-Dual-Port-by-RetroLink-NEW-/121101484855?pt=US_Audio_Cables_Adapters&hash=item1c32360337"), and [two units of this spare Genesis controller from Dx]("http://dx.com/p/additional-gamepad-controller-for-sku-28970-30530?rt=1&p=6&m=1&r=4&k=1&t=1&s=&u=30530").

Using this adapter, I can play fine a lot of games on my PC on Windows 7, but on Ubuntu I'm getting a strange issue: it's working fine on older Ubuntu versions, but not on newer ones.

I've tested it on Ubuntu 10.10 and 12.04, and everything was working as expected. But when I tested on Ubuntu 12.10 and 13.04, D-Pad Up and Left aren't responding. I checked output of "cat /dev/input/js0", and all buttons responded except for those two D-Pad directions. I'm guessing it's some kernel-related issue, since old Ubuntu versions aren't giving me any issues.

Anyone got a similar issue, or any workaround for this? Here's what "lsusb" returned for my device:

Bus 002 Device 012: ID 1292:4745 Innomedia

---

