---
title: "Deleted an item from taskbar... can't get it back! (WIreless internet)"
date: 2008-12-18
forum: General Help
---

### Post by d-d-d-d-d-d-card on 2008-12-18
Okay, I accidentaly wiped all the icons off my top taskbar today...

5 minutes of playing about and I solved my problem..
ONly issue is, and I hope you know what I'm talking about here..

The wireless internet icon which shows up on the top right of ubuntu, that gives updates on connection and stuff, and shows you when youre connected to the internet... is nowhere to be found.

DOes anybody know what the application is called or where to find it so I can make a shortcut again?

---

### Post by Izek on 2008-12-18
in terminal, run **nm-applet**.

---

### Post by PocketDog on 2008-12-18
It's called nm-applet, but it's probably your 'notification area' that's missing - add that, and your network manager applet should appear inside it.

---

### Post by d-d-d-d-d-d-card on 2008-12-18
Brilliant, cheers!

---

### Post by Izek on 2008-12-18
> **d-d-d-d-d-d-card said:**
> Brilliant, cheers!

if it doesn't appear when you reboot, you need to add the nm-applet to System > Preferences > Sessions, title it Network Manager Applet.

---

