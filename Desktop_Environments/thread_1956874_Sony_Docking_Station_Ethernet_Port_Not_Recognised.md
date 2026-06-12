---
title: "Sony Docking Station Ethernet Port Not Recognised"
date: 2012-04-11
forum: Desktop Environments
---

### Post by SolidSquid on 2012-04-11
So I decided to take the plunge and finally installed Xubuntu on my Vaio. It seems to be working pretty much 99%, but there are a couple of things bugging me. 

The main one is that the ethernet port for the docking station doesn't seem to be recognised by Xubuntu. I've tried plugging it directly into the laptop, and this works fine, but when the laptop is on the dock it's ethernet port is covered, and the whole point of the dock is to be able to get extra periferals/connections just by dropping the laptop on it. Does anyone know a way I could get this working? The USB ports seem to be recognised, and it picks up that the power cable is plugged in, so just seems to be ethernet

Thanks for any help you can give. Outside of this it looks great

EDIT: Solved the issue with compositing, just the ethernet issue left

---

### Post by SolidSquid on 2012-04-13
Anyone have any idea why the ethernet port wouldn't be recognised?

---

### Post by Kondor71 on 2012-08-02
hi,

how did you solve problems with usb and other... because in my sony it work fine only after reboot with plugged docking station...

---

### Post by iMurshaq on 2012-08-02
Please post output to:
```
lsusb
```

---

### Post by iMurshaq on 2012-08-02
Sorry also show this please:
```
hwinfo
```

---

### Post by Kondor71 on 2012-08-02
The problem is that after I plugged it dockstation all devices are listed in lsudb and lspci, but didn't work.

If I reboot all devices started to work... I can't understand why it didn't work in hot plug...


LSUSB before reboot [http://pastebin.com/jtra43vQ ]("http://pastebin.com/jtra43vQ")line 13 - my mouse plugged to dock and didn.t work

LSUSB after reboot [http://pastebin.com/5F3EqUXG](http://pastebin.com/5F3EqUXG) line 13 - my mouse plugged to dock but it works

LSPCI before reboot [http://pastebin.com/62grgzP5](http://pastebin.com/62grgzP5) lines 25-35 devices in dock, none of them works.

LSPCI after reboot [http://pastebin.com/ZWmUZTKg](http://pastebin.com/ZWmUZTKg) all works exept video card

So does anybody knows why it doesn't work after hot plug?

HWINFO before boot [http://pastebin.com/jcrT5Bys](http://pastebin.com/jcrT5Bys)

HWINFO after boot [http://pastebin.com/DsLZU3QD](http://pastebin.com/DsLZU3QD)

---

### Post by Kondor71 on 2012-08-02
dmseg after hotplug dock station

> [ 9233.063533] ACPI: \_SB_.DOCK - docking
[ 9233.064088] [Firmware Bug]: ACPI(GFXA) defines _DOD but not _DOS
[ 9233.064258] video: probe of LNXVIDEO:0a failed with error -5
[ 9233.064364] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[ 9233.064409] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[ 9233.064449] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[ 9233.064488] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[ 9233.064532] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[ 9233.064574] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[ 9233.064615] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[ 9234.045856] wlan0: no IPv6 routers present


---

