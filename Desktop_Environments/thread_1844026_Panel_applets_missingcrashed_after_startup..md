---
title: "Panel applets missing/crashed after startup."
date: 2011-09-14
forum: Desktop Environments
---

### Post by Lemvigh on 2011-09-14
Since I've installed 11.04, I have had the problem that almost every time I log in on my computer in classic mode, one or more applets are not present on the panel. I don't get any error messages, the applets are simply not there. The applets most frequently missing are Workspace Switcher, Show Desktop Button and Clock. 

I have not been able to find any mention of the problem in log files - but then again, I am not sure what log file to look in. 

As indicated above the problem is not consistent. Sometimes no applets are missing, sometimes several. I haven't found a pattern in when and which.

Any ideas what to look for?

Thanks!

---

### Post by Krytarik on 2011-09-14
Check the log file "~/.xsession-errors" in your home directory for relevant error messages after that happened the next time.

Good luck in tracking this down!

---

### Post by ccprog on 2011-10-15
I have the same problem; ~.xsession-errors says this:

```
** (gnome-panel:1585): WARNING **: Failed to load applet 
NotificationAreaAppletFactory::NotificationArea:
GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: 
Keine derartige Schnittstelle »org.gnome.panel.applet.AppletFactory« 
des Objekts im Pfad /org/gnome/panel/applet/NotificationAreaAppletFactory
```

I can see that there is a file
/usr/share/dbus-1/services/org.gnome.panel.applet.NotificationAreaAppletFactory.service
```
[D-BUS Service]
Name=org.gnome.panel.applet.NotificationAreaAppletFactory
Exec=/usr/lib/gnome-panel/notification-area-applet
```
and another one (leaving out localization lines)
/usr/share/gnome-panel/applets/org.gnome.panel.NotificationAreaApplet.panel-applet
```
[Applet Factory]
Id=NotificationAreaAppletFactory
InProcess=false
Location=/usr/lib/gnome-panel/notification-area-applet
Name=Notification Area Factory
Description=Factory for notification area

[NotificationArea]
Name=Notification Area
Description=Area where notification icons appear
Icon=gnome-panel-notification-area
BonoboId=OAFIID:GNOME_NotificationAreaApplet;OAFIID:GNOME_SystemTrayApplet;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gnome-panel
X-GNOME-Bugzilla-Component=notification area
X-GNOME-Bugzilla-Version=2.32.1
X-GNOME-Bugzilla-OtherBinaries=notification-area-applet
```
but no org.gnome.panel.applet.AppletFactory in any of the /usr/share/dbus-1 subdirectories or at /org/gnome/panel/applet. The binary is at /usr/lib/gnome-panel/notification-area-applet, as expected.

None of this gives any indication why most applets load, while it is completely random which of them does not.

---

