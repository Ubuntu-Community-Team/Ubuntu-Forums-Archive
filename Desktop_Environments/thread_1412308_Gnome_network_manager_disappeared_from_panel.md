---
title: "Gnome: network manager disappeared from panel?"
date: 2010-02-21
forum: Desktop Environments
---

### Post by Linux-Djihad on 2010-02-21
Hello,

today, suddendly the nm-applet icon (network-manager) disappeared from gnome panel, but I can't explain why. The network-manager seems to work. I got a connection and I even get the notification when I plug in the network cable, but the icon itself is gone.
I already searched for solutions but none of them work. 

/etc/xdg/autostart/nm-applet.desktop contains the following:

```

[Desktop Entry]
Name=Network Manager
Comment=Control your network connections
Icon=nm-device-wireless
Exec=nm-applet --sm-disable
Terminal=false
Type=Application
OnlyShowIn=GNOME;XFCE;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=NetworkManager
X-GNOME-Bugzilla-Component=general
X-GNOME-Autostart-enabled=true
X-Ubuntu-Gettext-Domain=nm-applet

```$ ps -eaf | grep Networkmanager | grep -v NetworkManagerDispatcher
markus    3220  2882  0 08:54 pts/0    00:00:00 grep --color=auto Networkmanager
markus@ubuntu /etc/dbus-1/event.d $ 

network-manager is launched:

```

$ ps -eaf | grep Networkmanager | grep -v NetworkManagerDispatcher
user1    3220  2882  0 08:54 pts/0    00:00:00 grep --color=auto Networkmanager

$ ps -eaf | grep nm-applet
user1   2735  2611  0 08:35 ?        00:00:00 nm-applet --sm-disable
user1   3223  2882  0 08:55 pts/0    00:00:00 grep --color=auto nm-applet

```A "$ restart network-manager" restarts it, but the icon is still missing. 

Any ideas?

---

### Post by Linux-Djihad on 2010-02-21
By the way, I don't even see the network connection status in conky system monitor.

---

### Post by Linux-Djihad on 2010-02-21
After reboot, the icon appeared but the conky still does not show any network activity although I download something. What going on here?

---

### Post by ajgreeny on 2010-02-22
I have no idea why this is, but I seem to suffer from the same problem, usually after a logout and login again.  nm-applet is still running according to System Monitor, so I stop it from there (or just **killall nm-applet** in terminal) and then start it again with Alt+F2 run dialog.  It must be stopped, and restarted for it to appear again, for some reason.

---

### Post by Linux-Djihad on 2010-02-22
Ok the conky problem is solved. I had a wrong configuration, because I'm using eth1 instead of eth0 now.
The nm-applet was not disappeared since last time, hmm.

---

