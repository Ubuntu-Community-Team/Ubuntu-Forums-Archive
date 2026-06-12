---
title: "ivtv and Hauppage PVR-150"
date: 2011-02-24
forum: Desktop Environments
---

### Post by spencerpants on 2011-02-24
Hi Folks,

I've been digging through Google a lot on this issue for a while, but no dice, so I figured I'd register and post here!  I have an old "Media Center" type tower from 2006 that I put Ubuntu on, and everything's been fine, but I can't seem to get the TV tuner working at all!

Configuration:
store-standard HP Pavilion m7480n tower
Hauppage WinTV PVR-150
Ubuntu 10.04
ivtv 1.4.0-1
mythtv 0.23.0+fixes24158-0ubuntu2

When I first installed ivtv, it seemed to go fine, and mythtv was able to detect my card and set up some stuff for it.  However, after I rebooted, mythtv couldn't find the card anymore.  When I dug a bit deeper, I saw that all the /dev/video* devices (previously video0, video24, and video32) were gone.

lspci still shows the card fine, but when I run dmesg | grep ivtv it displays the following:

[   19.440283] ivtv: Start initialization, version 1.4.1
[   19.440378] ivtv0: Initializing card 0
[   19.440383] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   19.448334] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   20.310932] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   23.900497] tuner 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   23.922647] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   23.926856] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   23.948041] IRQ 0/ivtv0: IRQF_DISABLED is not guaranteed on shared IRQs
[   23.948046] ivtv0: Failed to register irq -16
[   23.948693] ivtv0: Error -16 on initialization
[   23.948707] ivtv: probe of 0000:01:05.0 failed with error -16
[   23.948821] ivtv: End initialization

So my thoughts right now are that it's related to the ivtv driver, since it's fine at the PCI level and IVTV does detect the card on boot, just can't register it.  Thoughts?

Thanks a ton,
Spencer

---

### Post by spencerpants on 2011-02-24
also: I downloaded/installed both ivtv and mythtv just by using Ubuntu's software center, not anything else.

---

