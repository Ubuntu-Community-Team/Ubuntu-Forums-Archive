---
title: "Icons missing from panel"
date: 2009-01-09
forum: General Help
---

### Post by FreudianSlap on 2009-01-09
Hi everyone, I'm FreudianSlap - I'm an Ubuntu n00b so please be nice with me :)

When I first installed Ubuntu I had some icons on my panel for wireless network, battery level etc.  But now they have dissapeared.  I don't mean on the actual bar itself, (I can add and delete things from that) but the bit next to the clock.  (Kind of like the system tray on windows)  The only things in that 'tray' now are the clock and the volume control.  Can anyone advise me how I can get these icons back?

Thanks!

Freud.

---

### Post by jsroth on 2009-01-09
In the "tray" you're talking about only running processes are shown. When you're looking for the battery you should probably start the gnome-power-manager and for the wireless network it will probably be the nm-applet (either start them using ALT+F2 or add them to the auto started services).

---

### Post by sockrebel on 2009-01-09
the clock and volume control don't sit in the tray, they are on the panel itself.

1. you might have removed the "system tray" -
  -right click on panel -> "add to panel" -> "notification area" -> add

2. if the tray/notification area is already on your panel
  -to get battery level, "system"->"preferences"->"power management"->"general"->"always display" under notification area
  -to get wireless (assuming network manager), i think "nm-applet" as jsroth mentioned, should do it.

g'luck

---

