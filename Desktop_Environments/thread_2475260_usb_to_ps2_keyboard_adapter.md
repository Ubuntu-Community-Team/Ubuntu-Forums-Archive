---
title: "usb to ps2 keyboard adapter"
date: 2022-05-20
forum: Desktop Environments
---

### Post by bjlockie on 2022-05-20
I have an asrock b450m pro4 with one ps2 port (coloured purple and green).
I have a usb mouse and usb keyboard.
The goal is to power on with a ps2 keyboard.
I have a purple usb to ps2 adapter that I plugged the usb keyboard into and then connected to the motherboard.

The keyboard lights up (backlight) like it is connected but I can't type.

A. Do I possibly need a splitter cable?
B. Do I possibly need a green ps2->usb adapter (does the colour matter)?
C. Do I possibly need to reconfigure X?

---

### Post by GhX6GZMB on 2022-05-20
I'm confused. Why not just plug your USB keyboard into a USB socket? You have eight of them.

---

### Post by #&amp;thj^% on 2022-05-20
> **bjlockie said:**
> I have an asrock b450m pro4 with one ps2 port (coloured purple and green).
I have a usb mouse and usb keyboard.
The goal is to power on with a ps2 keyboard.
I have a purple usb to ps2 adapter that I plugged the usb keyboard into and then connected to the motherboard.

The keyboard lights up (backlight) like it is connected but I can't type.

A. Do I possibly need a splitter cable?
B. Do I possibly need a green ps2->usb adapter (does the colour matter)?
C. Do I possibly need to reconfigure X?

It depends entirely on the keyboard. Very old keyboards used 5 pin DIN (PC/XT/AT) or 6 pin miniDIN (PS2) plugs.
New ones use** USB.** At the time things started to migrate from miniDIN to USB, some keyboards had autosense circuity to allow use with either socket, providing an appropriate adapter is present.

---

### Post by bjlockie on 2022-05-20
> **ml9104 said:**
> I'm confused. Why not just plug your USB keyboard into a USB socket? You have eight of them.

I can't press a key to power on with USB, apparently USB is not monitored.

---

### Post by bjlockie on 2022-05-20
> **1fallen said:**
> It depends entirely on the keyboard. Very old keyboards used 5 pin DIN (PC/XT/AT) or 6 pin miniDIN (PS2) plugs.
New ones use** USB.** At the time things started to migrate from miniDIN to USB, some keyboards had autosense circuity to allow use with either socket, providing an appropriate adapter is present.

It's a Keychron K2 USB keyboard.
I am trying to use an adapter to plug it in the single PS2 port on the motherboard.

So I may not be able to use any USB keyboard with an adapter to PS2?

---

### Post by grahammechanical on 2022-05-20
You may need to enter system settings and select the PS/2 port (+ keyboard) as the input source.

Regards

---

### Post by #&amp;thj^% on 2022-05-20
> **grahammechanical said:**
> You may need to enter system settings and select the PS/2 port (+ keyboard) as the input source.

Regards
Good Idea. Worth a shot.

> **bjlockie said:**
> It's a Keychron K2 USB keyboard.
I am trying to use an adapter to plug it in the single PS2 port on the motherboard.

So I may not be able to use any USB keyboard with an adapter to PS2?
If the adapter didn't work, then there probably isn&#8217;t a way to use it. Unless you have Bluetooth on it.
Things like this can get you chasing adapters (not advisable), also do you have the manual for your MoBo, might take a peek at that.
No I'm not saying you can't use any USB keyboard, you'll have to dig deep to find one that has the "autosense"
EDIT: have a look at this: [https://www.amazon.com/StarTech-com-Replacement-USB-Keyboard-Adapter/dp/B000A0K2JO](https://www.amazon.com/StarTech-com-Replacement-USB-Keyboard-Adapter/dp/B000A0K2JO)
not sure what you have now.

---

### Post by bjlockie on 2022-05-23
The motherboard is [https://asrock.com/MB/AMD/B450M%20Pro4/index.us.asp](https://asrock.com/MB/AMD/B450M%20Pro4/index.us.asp)
The keyboard is [https://www.keychron.com/products/keychron-k2-wireless-mechanical-keyboard](https://www.keychron.com/products/keychron-k2-wireless-mechanical-keyboard)

I have an adapter like the Startech one.

---

### Post by guiverc on 2022-05-23
I've not commented on this thread as I've really had nothing concrete to offer.

I have noticed though that a software setup on one box, can have the machine wake up using keys on the keyboard; yet that same [*software*] setup + keyboard on another machine will not allow the machine to wake up.  I've taken it as just differences in hardware/firmware since in that case the software was identical (*clean install of system from same thumb-drive/ISO*). I've also noted some boxes will wake up if specific USB ports are used for keyboard (*on some USB ports I note USB keyboard LEDs dull to almost off; others they remain lit*; and here I'm talking BLACK USB ports, not blue/yellow). This is done as a mixture of me setting up my own machines, OR quality assurance which heavily involves Lubuntu.

I have little experience with PI & like *ARM *devices though, I'm referring to x86 (*i386 & amd64*) though in this comment.

---

