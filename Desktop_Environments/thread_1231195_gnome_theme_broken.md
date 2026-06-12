---
title: "gnome theme broken"
date: 2009-08-04
forum: Desktop Environments
---

### Post by hellz99 on 2009-08-04
I remoted into my machine today (yesterday it was fine) and all of a sudden my theme is looking wrong.  I'm still on human, but the look is more like default (no theme) gnome.  The windows look ok, but widgets in the top menu bar and buttons in the bar, and the separator look at jacked.  Same with buttons in the bottom task bar.

I'm also finding my screensaver isn't coming on when my timer hits, and if I click the "Lock Screen" button nothing happens.

I attached an image.

In the log I have this:
```

dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.73" (uid=1000 pid=8181 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.6" (uid=0 pid=6679 comm="/usr/lib/hal/hald-addon-storage "))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.73" (uid=1000 pid=8181 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.59" (uid=1000 pid=8154 comm="/usr/lib/gvfs/gvfs-gphoto2-volume-monitor "))
dbus-daemon: Rejected send message, 2 matched rules; type="method_call", sender=":1.73" (uid=1000 pid=8181 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.1" (uid=0 pid=5972 comm="/usr/sbin/console-kit-daemon "))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.73" (uid=1000 pid=8181 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.74" (uid=1000 pid=8117 comm="gnome-panel "))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.73" (uid=1000 pid=8181 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.57" (uid=1000 pid=8141 comm="/usr/bin/pulseaudio --start --log-target=syslog "))
dbus-daemon: Rejected send message, 2 matched rules; type="method_call", sender=":1.73" (uid=1000 pid=8181 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.11" (uid=0 pid=6779 comm="/sbin/wpa_supplicant -u -f /var/log/wpa_supplicant"))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.73" (uid=1000 pid=8181 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.55" (uid=1000 pid=8145 comm="/usr/lib/gvfs/gvfs-hal-volume-monitor "))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.73" (uid=1000 pid=8181 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.66" (uid=1000 pid=8118 comm="nautilus "))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.73" (uid=1000 pid=8181 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.43" (uid=0 pid=7396 comm="/usr/bin/python /usr/lib/system-service/system-ser"))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.73" (uid=1000 pid=8181 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.54" (uid=1000 pid=8087 comm="gnome-session "))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.73" (uid=1000 pid=8181 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.65" (uid=1000 pid=8163 comm="nm-applet --sm-disable "))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.73" (uid=1000 pid=8181 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.53" (uid=1000 pid=8094 comm="/usr/lib/libgconf2-4/gconfd-2 "))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.73" (uid=1000 pid=8181 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.64" (uid=1000 pid=8158 comm="/usr/bin/pulseaudio --start --log-target=syslog "))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.73" (uid=1000 pid=8181 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.52" (uid=0 pid=8037 comm="sshd: myuser[priv]"))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.73" (uid=1000 pid=8181 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.63" (uid=1000 pid=8166 comm="gnome-power-manager "))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.73" (uid=1000 pid=8181 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.62" (uid=1000 pid=8159 comm="/usr/lib/tracker/trackerd "))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.73" (uid=1000 pid=8181 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.73" (uid=1000 pid=8181 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a"))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.73" (uid=1000 pid=8181 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.50" (uid=0 pid=8001 comm="sshd: nx [priv]   "))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.73" (uid=1000 pid=8181 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.61" (uid=1000 pid=8156 comm="bluetooth-applet "))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.73" (uid=1000 pid=8181 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.72" (uid=1000 pid=8189 comm="/usr/lib/fast-user-switch-applet/fast-user-switch-"))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.73" (uid=1000 pid=8181 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.60" (uid=1000 pid=8130 comm="update-notifier --startup-delay=60 "))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.73" (uid=1000 pid=8181 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.70" (uid=1000 pid=8174 comm="/usr/lib/tracker/tracker-indexer "))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.73" (uid=1000 pid=8181 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.75" (uid=1000 pid=8099 comm="gnome-keyring-daemon --start "))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.73" (uid=1000 pid=8181 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.76" (uid=1000 pid=8147 comm="python /usr/share/system-config-printer/applet.py "))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.73" (uid=1000 pid=8181 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.77" (uid=110 pid=8256 comm="/usr/lib/policykit/polkitd "))


```

I tried rebooting since I havent in around 20 days, but it did nothing.  I deleted my .gnome folder from my home, did nothing.
Any ideas?

---

### Post by hellz99 on 2009-08-04
I have some additional information. 
As mentioned above, I noticed this problem while remoting into the machine via nxclient.  I just went and logged into the machine itself and I see no problems at all.  I decided to then try remoting again, and there still the problem.  It only seems to be when I'm remoting using nxserver.

Maybe I'll try X tunneling.

---

### Post by Aaron44126 on 2009-08-04
Same problem with me.  (In fact, I recently posted about it [here](http://ubuntuforums.org/showthread.php?t=1227186).)  Started about a week ago, after I rebooted from a kernel update.  I suspect a recent update broke it...  It wasn't the kernel update, I think it was another recent update but the "break" didn't take affect until I logged out and back in.  Been trying to fix it for a while with no luck.

I also am accessing my machine via NX.  I hadn't really thought that that could be the problem.  The machine is in a location where I cannot access it directly.

Let me know if you learn anything more (and I will do the same!).


[Edit]

I hadn't noticed the screen saver / lock screen not working.  I don't have a screen saver enabled on the machine (because I always run it in NX, having a screen saver only on the client is fine with me), but I tried the "Lock screen" command just now and nothing happened.

I have also been able to reproduce the problem on a brand new account, so I know it's not anything wrong with my GNOME profile.

---

### Post by Aaron44126 on 2009-08-04
Fixed.  gnome-settings-daemon was crashing, see [this bug](https://bugs.edge.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/199245).

Run gconf-editor.
Navigate to /apps/gnome_settings_daemon/plugins/keyboard.
Uncheck the "Active" box on the right.
Log out and log back in.

This disables the "keyboard" plug-in for gnome-settings-daemon.  I'm not exactly sure what this plug-in does at the moment, but my keyboard is still working fine.  :-P

---

### Post by hellz99 on 2009-08-05
Works!
Aaron, you are the man!

---

