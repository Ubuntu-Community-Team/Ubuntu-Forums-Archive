---
title: "Automatically Running a Shell Command on Login"
date: 2007-11-06
forum: Desktop Environments
---

### Post by IndyNosebone on 2007-11-06
I've just switched over from XP to Ubuntu, and have very little experience with Linux, let alone trying to do anything outside of the GUI. Here's my current issue:

I've just gotten my Airlink Wireless USB dongle to work using ndiswrapper and a WinXP driver, but every time I restart my computer, I have to manually open the terminal, and type
"sudo modprobe ndiswrapper" to let my computer access the wireless network, otherwise it is completely oblivious to the fact that the USB dongle is plugged in.

I was wondering if there is an automated way of having that command automatically execute upon login, or if there is another way around the problem that I'm having.

Thanks in advance!

---

### Post by bingoUV on 2007-11-06
> **IndyNosebone said:**
> I've just switched over from XP to Ubuntu, and have very little experience with Linux, let alone trying to do anything outside of the GUI. Here's my current issue:

I've just gotten my Airlink Wireless USB dongle to work using ndiswrapper and a WinXP driver, but every time I restart my computer, I have to manually open the terminal, and type
"sudo modprobe ndiswrapper" to let my computer access the wireless network, otherwise it is completely oblivious to the fact that the USB dongle is plugged in.

I was wondering if there is an automated way of having that command automatically execute upon login, or if there is another way around the problem that I'm having.

Thanks in advance!

enter this command in /etc/rc.local. This file is executed at boot time, after all usual initialization is done. Since it is run as root, you do not need the sudo part. Do the following :
```

sudo gedit /etc/rc.local

```

Edit the file so opened, In the end, add a line and add "modprobe ndiswrapper" and save the file. Reboot, and it should have detected the wireless.

---

### Post by IndyNosebone on 2007-11-06
Great!
Worked perfectly! Thank you so much! :-D

---

