---
title: "Properly disabling auto-mount in Ubuntu 14.04"
date: 2016-01-28
forum: Desktop Environments
---

### Post by DigiAngel on 2016-01-28
Try as I might I am just unable to disable USB devices from automounting.  Things I've done:

Checked "Never prompt or start programs on media insertion" in Removable Media settings

Set all to "Do nothing" in Removable Media settings

Added an entry to /etc/fstab as shown:
```
/dev/sde1        /media/usb6    auto            ro,users,noauto,noexec  0       0
```
but after inserting the USB drive I see:
```
/dev/sde1 on /media/usb6 type vfat (ro,noexec,nosuid,nodev)
```

Gone to org.gnome.desktop.media-handling in dconf-editor and unchecked automount

Created the file /etc/udev/rules.d/85-no-automount.rules that contains 'SUBSYSTEM=="usb", ENV{UDISKS_AUTO}="0"' and rebooted.

Nothing works.  As soon as I plug in a USB device Ubuntu automounts it happily.  How can I once and for all stop Ubuntu from automounting?  Thank you.

---

### Post by mc4man on 2016-01-28
What file manager & session are you using? Setting org.gnome.desktop.media-handling automount false works just fine here in an ubuntu session with nautilus

---

### Post by DigiAngel on 2016-01-28
Just the stock Nautilus...it's pretty crazy.

---

### Post by deadflowr on 2016-01-28
Is it opening a nautilus window or adding a launcher to the launcher bar, or it is simply listed in nautilus in the side panel?

When you set it not mount/automount, it'll still show up in the file manager, but without the mounted eject symbol.

---

### Post by DigiAngel on 2016-01-28
It's not launching, just mounting with the eject symbol in the side panel.  Thank you.

---

