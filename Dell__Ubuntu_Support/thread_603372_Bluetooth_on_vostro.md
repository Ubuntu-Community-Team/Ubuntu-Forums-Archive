---
title: "Bluetooth on vostro"
date: 2007-11-05
forum: Dell  Ubuntu Support
---

### Post by CuBone on 2007-11-05
I can't get the bluetooth adapter working on my vostro 1700. I made a fresh install of gutsy when it was released and everything is working (I think) except the bluetooth adapter. 

I tried this guide [https://help.ubuntu.com/community/BluetoothSetup]("https://help.ubuntu.com/community/BluetoothSetup") but the hcitool dev command doesn't  list any devices

```
hcitool dev
Devices:

```

Any suggestions on what I can try next?

---

### Post by plehman on 2007-11-05
I don't know if this will help you much or not, but I think I've got Bluetooth running pretty well on my machine (I really only wanted to get my bluetooth mouse working with my Vostro 1400).  

When I first installed the Feisty Fawn version, I then installed the following packages, which you may have already done:

bluez-utils
bluez-pin

Looking via the Synaptics Package Manager, I've also got the following installed:

bluemon
bluez-cups
bluez-gnome
libbluetooth2

Then I added a Bluetooth icon to the top menu bar.  It kinda worked under Feisty Fawn but I had to manually pair the mouse and such each time.  After upgrading to the new Ubuntu version, it happens automatically, exactly as I want it to.  that being said, I haven't tried to connect other Bluetooth devices to the machine (like a cell phone, headset, printer, etc.).

Hope that helps.

---

### Post by CuBone on 2007-11-06
Hade everything in that list installed except bluez-pin bluemon. But they seem to be  extensions to the bluetooth service not a way to get the bluetooth itself working.

---

