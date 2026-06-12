---
title: "Nvidia Graphics problem"
date: 2006-10-14
forum: Desktop Environments
---

### Post by 2pacalypse on 2006-10-14
I have an issue with the graphics drivers of Nvidia. everytime I install them, they boot up normally and work as they should. however after a reboot they stop working, after the ubuntu start up i see a black screen for 20 secounds and then my monitor turns off, to solve the problem i must remove the drivers, reboot get a X-server error screen, reinstall the drivers and then reboot again, but its driving me insane already cuz i have to do it like 5 times a day. Ive already tried to install the driver by using two diffrent scrips (Envy+nvidia-xconfig) and by manually (installing nvidia driver+manual editing of xorg.conf) but they all give the same result. further more, i have noticed another problem which started from the day i installed the drivers, everytime my computer runs over 10-15 hours strenight. he locks up and forces me to reboot. I think that its related to the Nvidia drivers but i have no way to be sure.
Can any1 please help me?

                              Thanks in Advance

---

### Post by aknapp on 2006-10-14
Any time you request help you should cite your model and versions, like; Videocard Manu and Model, Ubuntu version, Driver version, etc. The more info the better people can help you, probably.

The locking up after 10-15 hours doesn't sound like a driver issure to me, but more of a overheating one.

---

### Post by 2pacalypse on 2006-10-14
ok, the problematic Videocard is Nvidia Geforce 5200FX. i am running Ubuntu 6.06 (Dapper Drake). i dont recall the driver version but its the newest version. just downloaded it yesterday

---

### Post by Knowledge on 2006-10-14
> **2pacalypse said:**
> I have an issue with the graphics drivers of Nvidia. everytime I install them, they boot up normally and work as they should. however after a reboot they stop working, after the ubuntu start up i see a black screen for 20 secounds and then my monitor turns off, to solve the problem i must remove the drivers, reboot get a X-server error screen, reinstall the drivers and then reboot again, but its driving me insane already cuz i have to do it like 5 times a day. Ive already tried to install the driver by using two diffrent scrips (Envy+nvidia-xconfig) and by manually (installing nvidia driver+manual editing of xorg.conf) but they all give the same result. further more, i have noticed another problem which started from the day i installed the drivers, everytime my computer runs over 10-15 hours strenight. he locks up and forces me to reboot. I think that its related to the Nvidia drivers but i have no way to be sure.
Can any1 please help me?

                              Thanks in Advance

Hi there,

try following:

**1. Open your X11 config.**

On Terminal:
```

sudo nano -w /etc/X11/xorg.conf
```

**2. Put the following line between the *Device Section***

```
Option        "NvAGP"                 "0" # Disables AGP
```

And then restart your Computer or login to your X/KDE/GNOME whatever you have. After that tell us if it worked!!

---

### Post by 2pacalypse on 2006-10-14
ok, ive done it and it seems to be working

Thanks alot man, this is really really helpfull.

---

