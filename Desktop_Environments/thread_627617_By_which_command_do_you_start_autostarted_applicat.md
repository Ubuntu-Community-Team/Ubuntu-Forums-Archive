---
title: "By which command do you start autostarted applications."
date: 2007-11-30
forum: Desktop Environments
---

### Post by jis on 2007-11-30
In Xubuntu 7.10 I can set autostarted applications at Settings > Autostarted Applications. I can check, uncheck, remove and add applications, but I can not see what the actual command is. By which commad do you start Print Queue Applet, for instance? (I would like to use the applet when using IceWM window manager.)

---

### Post by TeaSwigger on 2007-11-30
> **jis said:**
> In Xubuntu 7.10 I can set autostarted applications at Settings > Autostarted Applications. I can check, uncheck, remove and add applications, but I can not see what the actual command is. By which commad do you start Print Queue Applet, for instance? (I would like to use the applet when using IceWM window manager.)

I have no idea lol. But I use fluxbox & IceWM on kubuntu, so I know a few. For instance, to invoke kubuntu's KPrintJobViewer one could use '/usr/bin/kjobviewer --all --show' in a menu command. It may not be possible to use some of the xfce applets afaik... any others you need?

A thought; what you could use for a command may be listed in top or htop in xubuntu once they're running.

EDIT: gnome's print queue control appears to be '/usr/bin/system-config-printer-applet --no-tray-icon' if that helps.

---

### Post by jis on 2007-12-02
Thanks TeaSwigger, maybe I'll use it without the option to get the tray icon when printing first time. You can hide it later by right-clicking, but I can get it back only by relogging to iceWM, if I hide it first.

Thanks for the hint about htop; I had never heard of it, but I had used top many times.

I suppose the applet some python program, as I see the following line in htop:
```
python /usr/share/system-config-printer/applet.py 
```

This is not IceWM specific, but If I could enable power management in the machine, I could power off more easily.  In the beginning of ubuntu bootup I get message, where it is told something like due to old bios version ACPI is not started and "acpi=force is required to enable ACPI". Then there is also apm, but I don't know which works better with the pc.

---

