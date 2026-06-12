---
title: "bluetooth pairing problem"
date: 2006-08-08
forum: Desktop Environments
---

### Post by rainbowjoshua on 2006-08-08
Okay, I'm still in Breezy for the moment, but I'm trying to get paired with my bluetooth headset (Jabra BT500).  When the headset is in pairing mode, kbluetoothd can see it (the gnome bluetooth stuff all seems to me to suck), but then whenever I try to connect to it, I get:

Bluetooth Monitor
Problem connecting with **device**
Pairing not allowed

I've seen some people report the same problem, but I haven't managed to find a solution.  Any help would be appreciated!  :)

Joshua

---

### Post by wieman01 on 2006-08-08
Can you tell us what Bluetooth Dongle you are using? Some are not "suitable" for Linux.

Could KBluetooth detect your device's MAC address? If not, then it's going to be tricky.

---

### Post by rainbowjoshua on 2006-08-08
Oh, the dongle is definitely detected, as it can see our bluetooth phones and when the headset is in pairing mode, it sees it too.  The make is a "Zonet" although I can't remember the model.

I have made some progres now.  I changed the /hcid.conf security from "user" to "auto" and now it DOES prompt me for a pin, and I enter the appropriate pin and then konqueror shows me the contents of the device.  However, under the kbluetoothd "connection detals" I see no connection, and when I try to run btsco -v addr I get:

btsco v0.42
Device is 1:0
Error: Failed to connect to SDP server: Permission denied
Assuming channel 2

Voice setting: 0x0060
Can't connect RFCOMM channel: Permission denied

And then I get a funky sound and a kde "Authentication Error" dialog.  I don't think it's actually pairing for some reason.  Any ideas?
Thanks!

---

### Post by niteblind on 2006-08-13
hi

not sure if this is gonna help u but i just got around the same problem by entering this.

```
xhost +
```

This came back stating that devices from any host can now connect. Prior to doing this i was getting errors when trying to pair anything to the PC.

Hope it helps
niteblind

---

