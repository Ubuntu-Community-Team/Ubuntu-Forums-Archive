---
title: "bluetooth in lat d410"
date: 2008-01-25
forum: Dell  Ubuntu Support
---

### Post by fdofdo on 2008-01-25
I have a latitude D410 but I'm not able of making bluetooth work. I install bluez and gnome-bluetooth, but even though the "bluetooth light" turns on (not blinking but permantly until I switch it off) the phone doesn't recognize the laptop (but it recognize it when I use Win XP or other laptops) and the laptop doesn't reconize anything... any idea?

---

### Post by g0bl1n on 2008-02-04
I'm having the same problem. I don't have a windows partition so can't use the workaround that's been described elsewhere.

1. hcitool dev is returning nothing except "DEVICES:"
2. dmesg |grep "HID" is returning;
[22.344000] Bluetooth: HIDP (Human Interface Emulation) ver 1.2

...but I'm guessing this is software as opposed to hardware?

I have installed bluez-pcmcia-support bluez-utils gnome-bluetooth gnome-vfs-obexftp...

I've been searching all sorts of groups and posts but none of the options seem to work on my d410. Is this a historical problem? I've only just bought the laptop and installed Gutsy.

Any help would be greatly appreciated,

g0bl1n:confused:

---

### Post by BNix on 2008-03-06
Having this same issue. I don't see a bluetooth device @ all running lspci. Any idea how I could compile the Lat D410 Bluetooth driver, insmod it maybe?

Any help would be much appreciated!

:(

---

### Post by alpapan on 2008-06-27
Same problem here...

---

