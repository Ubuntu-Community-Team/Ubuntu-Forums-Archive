---
title: "I can't get my gamepad to work"
date: 2007-01-10
forum: Gaming &amp; Leisure
---

### Post by tee2 on 2007-01-10
This is my dmesg 
```
[17193087.384000] usb 4-2: USB disconnect, address 2
[17193138.540000] usb 4-2: new low speed USB device using uhci_hcd and address 3
[17193138.716000] usb 4-2: configuration #1 chosen from 1 choice
[17193138.740000] input: SealieComputing SuperRetroPad as /class/input/input6
[17193138.740000] input: USB HID v1.00 Gamepad [SealieComputing SuperRetroPad] on usb-0000:00:1d.3-2

```

In snes9xexpress you're supposed to select the device which the default is /dev/js0. I did a ls /dev and there isn't a /dev/js0, or a /dev/input6. What am I doing wrong?

---

### Post by po0f on 2007-01-10
tee2,

You have two options: you can either change the option in snes9xexpress to point to /dev/input/js0 (which should be created for you) or you can create a symlink from /dev/input/js0 to /dev/js0.  I don't use snes9xexpress so I don't know if you can change the option; I don't see why you wouldn't be able to though.

---

### Post by tee2 on 2007-01-10
Thanks, I just pointed snes9express to /dev/input/js0.

---

