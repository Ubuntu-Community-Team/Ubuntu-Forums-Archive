---
title: "Many Hang-ups on start up"
date: 2006-07-12
forum: Desktop Environments
---

### Post by RyanTrip on 2006-07-12
[dell web pc, 433 mhz, 190 mb ram]
I just installed linux on my pc (xubuntu) and it would get hung up during loading hardware drivers. I loaded the GNU GRUB and did "recovery mode" boot to try to pin pount the problem. This is where it got hung up most of the time:

[b]
[ 104.112380] 0000:01:0a.0: 3Com PCI 3c556 Laptop Tornado at cc8be400. Vers LK1.1.19
[/b]

I'm guesing somethings wrong with my ethernet card? But whats really odd is that it said laptop, and im running a desktop.

It also sometimes gets hung up on this too:

[b]
[ 217.335546] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[/b]

and this... :(

[b]
[ 216.569003] intel8x0: clocking 4800
[/b]

and last but not least, it sometimes complains somthing about my speakers. I don't renember the error.

this is my first time installing linux, in im kinda frustrated. windows 98 works fine befor I installed this, so I don't think its my hardware. I may still be incorrect. Does anyone know how to fix this? ](*,)

---

### Post by Paul Gilster on 2006-07-13
Same problem here, even with the latest updates. About one startup out of three I get frozen at "Loading hardware drivers." But if I reboot, I often get right past the hardware driver stage with no problems.

---

