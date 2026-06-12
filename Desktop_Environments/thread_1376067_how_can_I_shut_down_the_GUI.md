---
title: "how can I shut down the GUI?"
date: 2010-01-08
forum: Desktop Environments
---

### Post by yanvolking on 2010-01-08
Hello Community,

I often work in CLI and don't really need the GUI which uses up computer resources for nothing.  Is there a way of shutting down the GUI (I work in Ubuntu 9.10) but leaving the tty shell session active (working in CLI)?

Thanks

---

### Post by garryknight on 2010-01-08
You could log out so that your Gnome desktop isn't running, then press Ctrl+Alt+F1 (or Ctrl+Alt+ any of F2 to F6) to get to a text-based CLI. The DM login screen will still be running but won't use anything like as many resources as your desktop.

---

### Post by VCoolio on 2010-01-08
Hit ctrl+alt+f1 and run "sudo service gdm stop"

If you edit /etc/default/grub and change the line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash text"
and run "sudo update-grub" you'll boot to console.

---

### Post by SalahTr on 2010-01-08
Hi,
[http://ubuntuforums.org/showthread.php?t=1374824&highlight=gnome]("http://ubuntuforums.org/showthread.php?t=1374824&highlight=gnome")

---

### Post by Leppie on 2010-01-09
best is to edit the upstart gdm.conf file:
```
gksudo gedit /etc/init/gdm.conf
```
edit "start on" section to something like this:
```
start on (runlevel [345]
	  and filesystem
	  and started hal
	  and tty-device-added KERNEL=tty7
	  and (graphics-device-added or stopped udevtrigger))
stop on runlevel [0126]
```
like this you should boot into runlevel 2 (default runlevel) with cli, also changing to runlevel 2 will automatically kill your x session.
alternatively, you could set it to be active in runlevel 2 and to not activate in for example runlevel 3 and have the x session killed when changing to runlevel 3.

---

