---
title: "Dual Shock 2 works in Windows, not in Ubuntu"
date: 2006-07-19
forum: Gaming &amp; Leisure
---

### Post by hugh on 2006-07-19
Hello folks, I'm having some control pad issues. I have a Dual Shock 2 (PS2 controller) with a USB adapter. This works perfectly in Windows on this same computer, but on Ubuntu 6.06 it... doesn't.

When I plug it in, dmesg returns this:

```
[17179740.912000] usb 2-1: new low speed USB device using uhci_hcd and address 4[17179741.164000] usb 2-1: string descriptor 0 read error: -32
[17179741.180000] usb 2-1: string descriptor 0 read error: -32
[17179741.196000] usb 2-1: string descriptor 0 read error: -32
[17179741.196000] usb 2-1: configuration #1 chosen from 2 choices
[17179741.248000] usb 2-1: string descriptor 0 read error: -32
[17179741.256000] input: HID 0925:8866 as /class/input/input6
[17179741.256000] input: USB HID v1.00 Joystick [HID 0925:8866] on sb-0000:00:1d.1-1

```

Also, /dev/input/js0 is created, so I guess Ubuntu is aware a joystick-like device has been plugged in.

Any advice would be appreciated. Thanks.

---

### Post by eqisow on 2006-07-19
I'm not sure what to tell you. I use both a Dual Shock and a GC remote on Kubuntu with a [Trio linker Plus]("http://www.lik-sang.com/info.php?category=76&products_id=4532&") and have no problems.

If you have other gamepads, do they work? Maybe it's not an issue with the Dual Shock specifically.

---

### Post by vem0m on 2006-07-19
i bought me a cheap controller at wally world(wal-mart for those proper ppl out there) and it works fine :P even has the shakey shakes to it(ok i know i sound stupid :P)

---

