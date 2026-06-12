---
title: "dell d630 moving pointer"
date: 2010-02-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mch0lic on 2010-02-06
Hi

I have this really really really really annoying problem. My mouse cursor sometimes starts moving up or down and I can't move against it with any of devices available (touchpad, joystick or usb mouse). In the end I cant use pc. I tried to replug keyboard in motherboard but it doesn't help at all. Moreover even if I restart pc it doesnt help much...

This is a bit tricky coz I don't have a clue which device is not working in the way it should and xorg.conf is no longer available.

xinput list is attached.

Can I have any tips how to solve this sick problem?

Mindo

---

### Post by Cl0ud9 on 2010-02-07
I used to have this same problem and came up with a very simple solution.

Using xinput you want to turn off the entry labeled "DualPoint Stick". In your list it is entry 8.

Here's how:

To turn off the stick
```

xinput set-int-prop 8 "Device Enabled" 8 0

```

To turn it back on
```

xinput set-int-prop 8 "Device Enabled" 8 1

```

The 8 after set-int-prop is the device entry. In this case that 8 refers to your stick.

I suggest making two alias' in your .bashrc (or whatever shell you are using) so you can turn it on or off without typing out the full command each time.

Edit:

If you want to disable it on startup add an entry in System -> Preferences -> Startup Applications.

---

### Post by mch0lic on 2010-02-08
Huge thanks :)

I own u a beer

Mindo

---

