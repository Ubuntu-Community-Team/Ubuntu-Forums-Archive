---
title: "odd problem with mounting removable devices"
date: 2013-05-20
forum: Desktop Environments
---

### Post by toothandnail on 2013-05-20
Recently installed Xubuntu 13.04 on two machines, one for a customer and one on my own Lenovo laptop. This problem occurs on both machines.

When I plug in a removable device (either a flash drive or a USB hard drive), it will mount and open Thunar. Once. Next time I plug the same device in, it appears on the desktop, but does not mount, so Thunar never opens. Checking Settings > Removable Drives and Media, it is set to mount removable drives when hot plugged, mount removable media when inserted and browse removable media when inserted.

I'm a long term Xfce user (starting with Zenwalk, currently mainly running Arch), and I've not seen this behaviour on any other Xfce setup. Not sure where I should be reporing the bug, and I'm wondering if its anything to do with my setup (though that seems to be unlikely, given that its happening on two different installations).

Paul.

---

### Post by Dennis N on 2013-05-20
Well, I've seen the same behavior with Xubuntu 13.04, so I doubt it's your setup at all. I noticed more than once a USB stick not mount when plugged in the **first** time as well, and as you say the icon appears on the desktop as "not mounted". This is irregular, and more often than not, it mounts and opens with Thunar as it should.

Just to add, it happened yesterday with Xubuntu **12.10** as well. I plugged in one usb stick, and it did not mount, but displayed an icon on the desktop. Plugged in a second usb into another port (without removing the first) and the second stick mounted and opened in Thunar. Removed them both, tried again, and this time both mounted and opened in Thunar.

---

### Post by toothandnail on 2013-05-21
Since I was seeing the same behaviour on two different Xubuntu installations, I didn't think it was likely to be my setup - thought I'd check anyway.

Guess I'll have to look into filing a bug report. Thanks for the confirmation.

Paul.

---

