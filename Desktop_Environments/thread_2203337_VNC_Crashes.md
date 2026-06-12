---
title: "VNC Crashes"
date: 2014-02-02
forum: Desktop Environments
---

### Post by gopukrishnan on 2014-02-02
Hi,

I have a ubuntu 12.10 server in which I have installed Tightvnc. I am able to connect in to the server from a windows machine through vnc client but the connection is not presistant. It crashes intermittently. I can recreate the issue by accessing the firefox while I am already connected in by vnc. To connect again, i need to restart the service.

See below the log :

/home/user/.vnc/server1.log

unity-2d-panel: [WARNING] unity-2d-panel: Fatal IO error: client killed
unity-2d-shell: [WARNING] unity-2d-shell: Fatal IO error: client killed

(gnome-settings-daemon:70648): Gdk-WARNING **: gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.

Window manager warning: Fatal IO error 11 (Resource temporarily unavailable) on display ':1'.

(nautilus:70674): Gdk-WARNING **: nautilus: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.


(polkit-gnome-authentication-agent-1:70670): Gdk-WARNING **: polkit-gnome-authentication-agent-1: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.


(gnome-fallback-mount-helper:70676): Gdk-WARNING **: gnome-fallback-mount-helper: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.

gnome-session[70637]: Gdk-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.


(gdu-notification-daemon:70865): Gdk-WARNING **: gdu-notification-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.


(bluetooth-applet:70671): Gdk-WARNING **: bluetooth-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.


(software-center:70889): Gdk-WARNING **: software-center: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.


(nm-applet:70677): Gdk-WARNING **: nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.


(telepathy-indicator:70866): Gdk-WARNING **: telepathy-indicator: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.



Please advise.

---

### Post by Kirboosy on 2014-02-03
I see complaints online about tightvnc crashing on Ubuntu but no solutions. I would recommend switching to UltraVNC or another VNC. See if your mileage varies with another version.

[VNC Crashes]("http://ubuntuforums.org/showthread.php?t=1353894")
[TightVNC Segfaults]("http://ubuntuforums.org/showthread.php?t=1396744")
[VNC Crashes cutting and pasting]("http://ubuntuforums.org/showthread.php?t=1450093")

Hope that helps!
~Caboose

PS Please use the code tags when pasting any code. It makes it easier to read and its easier to tell that is code. You can find them by clicking on the **#** in the text editor

---

