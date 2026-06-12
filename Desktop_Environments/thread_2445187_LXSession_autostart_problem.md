---
title: "LXSession autostart problem"
date: 2020-06-10
forum: Desktop Environments
---

### Post by jet-bundle on 2020-06-10
I have an old HP Pavilion dm1 laptop; one OS on this is Lubuntu 18.04. The machine has a touch-screen with a known bug, that sometimes the left-hand side of the screen can start to register spurious inputs, so that the pointer jumps around. So I need to disable the touch-screen. I can do this with xinput, using either the device id or the device name, as follows:
```

xinput disable 9
xinput disable[COLOR=#000000] “Atmel Atmel maXTouch Digitizer”[/COLOR]

```
I want to do this automatically on start-up, so I've set the LXSession configuration, adding one or other as a manual autostart application. The problem is that using the device name doesn't work. Using the device id does work, but if I start the machine with an external mouse plugged into a USB port then this takes over id 9 and so the mouse is disabled on startup rather than the touchscreen.

Is there any obvious reason for the device name not working with xinput used as a startup application, when it works with xinput used in a terminal window? Any suggestions on a work-around would be appreciated.

---

