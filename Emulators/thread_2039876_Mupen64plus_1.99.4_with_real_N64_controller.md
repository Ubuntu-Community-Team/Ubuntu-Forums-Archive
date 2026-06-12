---
title: "Mupen64plus 1.99.4 with real N64 controller"
date: 2012-08-09
forum: Emulators
---

### Post by k1piee on 2012-08-09
Hi,

I'm running Ubuntu 12.04 64-bit with Mupen64plus 1.99.4 with a N64-adapter, this one: [http://www.retrousb.com/product_info.php?cPath=21&products_id=82](http://www.retrousb.com/product_info.php?cPath=21&products_id=82), and I'm trying to get the controller to work but I can't.

The controller isn't recognized automatically and jumps straight to the keyboard. I've tried this config: [http://0-code.google.com.library.metmuseum.org/p/mupen64plus/wiki/ControllerSetup](http://0-code.google.com.library.metmuseum.org/p/mupen64plus/wiki/ControllerSetup) but the mapping is all out of wack, left-C is Start or A and the D-pad is mapped to some other button.

The game starts and all and works fine, it's just the controller that I can't get working properly. Can anyone help me here? Or has maybe anyone else got this working?


Thanks,

---

### Post by k1piee on 2012-08-10
I found 'jstest-gtk' which helped me find out which buttons are mapped to what number. So I finally mapped everything out correctly :)

This is the config for the adapter from retrousb.com:

```

[SealieComputing N64 RetroPort]
plugged = True
plugin = 2
mouse = False
AnalogDeadzone = 0,0
AnalogPeak = 12767,12767
DPad R = button(0)
DPad L = button(1)
DPad D = button(2)
DPad U = button(3)
Start = button(4)
Z Trig = button(5)
B Button = button(6)
A Button = button(7)
C Button R = button(8)
C Button L = button(9)
C Button D = button(10)
C Button U = button(11)
R Trig = button(12)
L Trig = button(13)
Mempak switch =
Rumblepak switch =
X Axis = axis(0-,0+)
Y Axis = axis(1-,1+)

```

It works fine for me, I'm plying Zelda right now :)
Hope someone finds this useful!

---

