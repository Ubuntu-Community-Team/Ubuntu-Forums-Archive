---
title: "Multiple X servers"
date: 2009-06-21
forum: Desktop Environments
---

### Post by zkab on 2009-06-21
Had some problems going from 8.10 -> 9.04 with my onboard Nvidia GeForce 6150 ... this is the first time I run into difficulties with Nvidia ... got a black screen with a cross ...
After some Google-ing I followed the guidelines in [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual) and now I guess that I am closer to the finish line ... after a boot I receive (after Ubuntu/Nvidia splash) a window telling me that 'There already appears to be an X server running on display :0. Should another display number by tried? ...'

Whatever I answer I can't get around this message ... /etc/X11/xorg.conf and /var/log/Xorg.0.log seem to be OK

What's wrong ?

---

### Post by cariboo on 2009-06-21
Personally I would move your /etc/X11/xorg.conf to a backup and start without one, then use System-->Administration-->Hardware drivers and install the recommended drivers:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

---

### Post by zkab on 2009-06-22
The problem is that I don't get any GUI ...

---

### Post by Nythain on 2009-06-22
what happens if you hit ctrl alt f2, log in, and type
sudo /etc/init.d/gdm restart
you can replace gdm with kdm if you use kdm instead (kde's display manager)

---

### Post by zkab on 2009-06-24
It says that Gnome Display Manager starts but I don't get any GUI in anywhere ...

---

