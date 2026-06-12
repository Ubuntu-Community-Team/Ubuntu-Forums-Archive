---
title: "Street Fighter IV FightStick xbox 360"
date: 2009-06-03
forum: Gaming &amp; Leisure
---

### Post by Adrijang on 2009-06-03
Hi!

Got Hardy 8.04.
I use a PS2 joystick with an adapter to play on sdlmame. Works perfect.

I recently got the street fighter IV fightstick for xbox 360 and did the installation for the xbox360 controller.

It doesn't work.

Anybody knows how to make it so?

Thanks

---

### Post by ruzkie on 2009-06-03
what do you mean did the installation? also how dosen't it work, be more specific.

---

### Post by Adrijang on 2009-06-03
> **ruzkie said:**
> what do you mean did the installation? also how dosen't it work, be more specific.

Did this: [https://help.ubuntu.com/community/Xbox360Controller](https://help.ubuntu.com/community/Xbox360Controller)

The green xbox light doesn't stop blinking and it doesn't recognize the controller on jscalibrator.

dmesg says this: 

[ 4573.043265] usb 3-2: new full speed USB device using uhci_hcd and address 5
[ 4573.059615] usb 3-2: configuration #1 chosen from 1 choice

It works on windows after autoinstalling the drivers.

---

### Post by Vitamin-Carrot on 2009-06-04
[quote[ It works on windows after autoinstalling the drivers.[/quote]

:-?

Well at least you know the fault isnt hardware based ...

Is it not your standard 360 controller?

---

### Post by Adrijang on 2009-06-04
> **Vitamin-Carrot said:**
> 

Well at least you know the fault isnt hardware based ...

Is it not your standard 360 controller?

That's the problem. It's an arcade stick, not even from Micro$oft but from Madcatz.

I found that on Mac Os X works with the standard drivers after a few modifications of a file, maybe it has something to do with my problem:

[http://forums.shoryuken.com/archive/index.php/t-178075.html](http://forums.shoryuken.com/archive/index.php/t-178075.html)

---

### Post by Adrijang on 2009-06-07
I added a line on xpad.c:

{ 0x4718, 0x0738, "SF4 Stick", GAMEPAD_XBOX360 },

those hexadecimal are idProduct and idVendor

Cleaned, compiled, added the driver and it still doesn't work.

Damn!!

---

### Post by Adrijang on 2009-06-14
I tried a normal xbox360 controller and it worked.

Daaaaaaammmmnnnn

---

### Post by rupert on 2010-08-22
any news on this, would like to use the stick with ubuntu.

---

