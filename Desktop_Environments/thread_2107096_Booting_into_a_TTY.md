---
title: "Booting into a TTY"
date: 2013-01-21
forum: Desktop Environments
---

### Post by Arashaun42 on 2013-01-21
Hello, to begin with sorry if this is in the wrong place, feel free to move it.

I am wondering if there is a way to automatically boot into a TTY terminal when I turn on my laptop. I am running 12.04, with Gnome 3 as my main enviroment.

I would ideally like Gnome 3 or any type of graphical interface to not start automatically, and instead just have a TTY, and be able to start a GUI session through some sort of command when it suits.

Sorry if I am being nclear, thank you for your help

---

### Post by The Cog on 2013-01-21
Edit the file /etc/init/lightdm.conf and comment out the "start on" section (lines 11-16) so it looks like this:```
#start on ((filesystem
           #and runlevel [!06]
           #and started dbus
           #and (drm-device-added card0 PRIMARY_DEVICE_FOR_DISPLAY=1
                #or stopped udev-fallback-graphics))
          #or runlevel PREVLEVEL=S)

```
You will need to do this under sudo on order to gain the required access rights. On a tty, use the command ```
sudp nano /etc/init/lightdm.conf
``` or in a GUI you can do ```
gksu gedit /etc/init/lightdm.conf
```
Then to start/stop the desktop manager manually, 
```
sudo service lightdm start
sudo lightdm service stop
```

---

