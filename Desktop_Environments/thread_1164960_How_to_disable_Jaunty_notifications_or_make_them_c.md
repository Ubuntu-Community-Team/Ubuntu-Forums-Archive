---
title: "How to disable Jaunty notifications or make them close automaticaly?"
date: 2009-05-20
forum: Desktop Environments
---

### Post by rrwo on 2009-05-20
The notifications in Jaunty are really annoying: when I resume my laptop, there is a notification about the wireless being disconnected (presumably from when I shut the laptop down). Worse, it doesn't close automatically.

Similar for battery is charged notification: I want it to go away on its own after a few seconds.

How do configure notifications so that they close by themselves?

---

### Post by Ausmosis on 2009-05-20
> **rrwo said:**
> The notifications in Jaunty are really annoying: when I resume my laptop, there is a notification about the wireless being disconnected (presumably from when I shut the laptop down). Worse, it doesn't close automatically.

Similar for battery is charged notification: I want it to go away on its own after a few seconds.

How do configure notifications so that they close by themselves?

You can get rid of the notifications which is what I did. Your notifications will then revert back to the way it was in previous versions prior to Jaunty. I hated the new notification system because you can't configure it. Apparently this option will come in the next version of Ubuntu but how configurable I don't know.

If you want to delete the current notifications then simply type the following in a terminal:

sudo apt-get remove notify-osd

---

### Post by Brandon Williams on 2009-05-20
There are some packages that depend on 'notification-daemon', which is provided by notify-osd. The two on my xubuntu system are update-notifier and gnome-power-manager, both of which are recommended by xubuntu-desktop. If you want to get rid of notify-osd, then you'll also need to remove any of its dependencies. If you don't want to lose the dependent components, then I suggest you install either notification-daemon or xfce4-notifyd as a replacement for notify-osd.

---

### Post by rrwo on 2009-05-20
Two solutions: to *disable* notifications, use
```
cd /usr/share/dbus-1/services/
sudo mv org.freedesktop.Notifications.service org.freedesktop.Notifications.service.disabled
```
rather than uninstalling them and dealing with dependency issues;
or you can try configuring them. Since I'm using Xfce,
```
xfce4-notifyd-config
```
does the trick. It supposedly defaulted to disappear after 10 seconds, but running the configuration seemed to actually make it use that setting.

---

### Post by richard.e.morton on 2009-09-29
nope; on Karmic that didn't work. xcfe4-notify-config is not installed.

I have also removed notify-osd (but not rebooted) and it is still there.

I am using the system as a mythtv-frontend and the popups occur when mythtv changes the volume - but myth already has a osd so it isnt needed. any ideas to get rid of the XCFE / XUBUNTU OSD?

thanks

R

---

### Post by bagy on 2009-10-04
Go to Settings --> Session and startup Application Autostart tab and uncheck xfce4-tips

---

### Post by gchatzim on 2010-03-22
I could not disable the notifications by renaming the files in the dbus-1/services folder.
I am on karmic koala. any suggestions?

---

### Post by antidrugue on 2012-03-17
> **rrwo said:**
> Since I'm using Xfce,
```
xfce4-notifyd-config
```
does the trick. It supposedly defaulted to disappear after 10 seconds, but running the configuration seemed to actually make it use that setting.

That really did the trick for me in Xubuntu 12.04. It is possible to configure the number of seconds (3 seconds seems more reasonnable than the default 10).


Also, one can use the "Gconf" system to configure notifications for a particular application. For example, to change settings for Network-Manager, one can edit the following file:

```
~/.gconf/apps/nm-applet/%gconf.xml
```

And put lines such as those inside the [gconf] tags:
```
<?xml version="1.0"?>
<gconf>
<entry name="disable-vpn-notifications" mtime="1331961392" type="bool" value="true"/>
<entry name="disable-connected-notifications" mtime="1331597917" type="bool" value="true"/>
</gconf>
```

The value of "mtime" is irrelevant. The "gconf-editor" can also be used to simplify the configuration of those applications ("gconf-editor" is not installed by default however).

---

### Post by coffeecat on 2012-03-17
Old thread - closed.

---

