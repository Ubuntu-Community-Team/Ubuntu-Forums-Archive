---
title: "How to disable gnome startup ?"
date: 2011-01-06
forum: Desktop Environments
---

### Post by Ghost_Mazal on 2011-01-06
Lo Guys ,

I want to disable the graphical desktop automatically starting up at boot. I want it to boot only to terminal. I don't want to remove it completely and still want to be able to start it up with for example "startx" if I need it.

Can this be done ? And if yes how ?

Thanx

---

### Post by amsterdamharu on 2011-01-06
Try this command:
> sudo nano /etc/init/gdm.conf 
The part:
```
start on (filesystem
          and started dbus
          and (drm-device-added card0 PRIMARY_DEVICE_FOR_DISPLAY=1
               or stopped udevtrigger))

```
Can be replaced by:
```
start on (start-gdm)
```

To start the graphic login and gnome you can give the following command:
```
sudo service gdm start
```
To stop it:
```
sudo service gdm stop
```

---

### Post by pavi_elex on 2011-11-08
Disable GDM-
sudo update-rc.d -f gdm remove
enable GDM-
sudo update-rc.d -f gdm defaults

---

