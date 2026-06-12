---
title: "~30s from login to usable...help reading bootchart"
date: 2012-05-07
forum: Desktop Environments
---

### Post by coleman_ian on 2012-05-07
I have a problem where I log in and it takes about 30s from entering the password to having anything come up on the desktop. This only happened recently and happens every time I log in. I used to have a usable desktop within less than a second (SSD is great).

I followed the instructions for bootchart from here
[http://askubuntu.com/questions/90076/slow-boot-login-how-do-i-figure-out-the-cause](http://askubuntu.com/questions/90076/slow-boot-login-how-do-i-figure-out-the-cause)

but I have no idea how to read the chart. I can see a lot of processes that may have been the cause. Can anyone help me figure out what to do to prevent this slow login from happening?

My bootchart is here
[http://i.imgur.com/vVGZy.png]("http://i.imgur.com/vVGZy.png")

---

### Post by Toz on 2012-05-08
If you then logout and log back in again, is there still a 30s delay. If there is, it may not be related to the boot process (and the botchart won't help).

If the delay persists, can you post back the contents of your ~/.xsession-errors file?

Also, have you added anything to the autostart applet?

And finally, you might also consider cleaning out your sessions cache - perhaps something in there is clogging it up. From a terminal:
```
rm -rf ~/.cache/sessions
```
...and try rebooting to see if theres a difference.

---

### Post by coleman_ian on 2012-05-08
I logged out and there was a long delay at logout, and then I logged back in but still with the same long delay.

I have added three things to the autostart myself:
xrandr --output LVDS1 --left-of --HDMI1
xbacklight -dec 100
rfkill block bluetooth

1) Because my dual monitor setup doesn't work properly without this command
2) Because my laptop backlight defaults to full brightness and I always work with it at very low brightness
3) Because bluetooth is on by default and I don't use it.

Also dropbox has automatically added an entry into my startup which I have left enabled:
dropbox start -i

The rest of the autostart seems like system default startup commands.

I cleaned out my sessions cache with the command provided but after restarting the delay at login was still there.

This is the output of ~/.xsession-errors

Thanks for the help so far.

```
openConnection: connect: No such file or directory
cannot connect to brltty at :0
xrdb:  "Xft.hinting" on line 13 overrides entry on line 6
xrdb:  "Xft.hintstyle" on line 14 overrides entry on line 7
xrandr: cannot find output "--HDMI1"
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-1vZ0pa/pkcs11: No such file or directory

(polkit-gnome-authentication-agent-1:2430): GLib-CRITICAL **: g_variant_new_string: assertion `string != NULL' failed

(polkit-gnome-authentication-agent-1:2430): polkit-gnome-1-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
** Message: applet now removed from the notification area
** Message: using fallback from indicator to GtkStatusIcon
** Message: applet now embedded in the notification area

(xfce4-indicator-plugin:2603): libindicator-WARNING **: IndicatorObject class does not have an accessible description.

(xfce4-indicator-plugin:2603): libindicator-WARNING **: IndicatorObject class does not have an accessible description.
** Message: moving back from GtkStatusIcon to indicator
** Message: applet now removed from the notification area

(xfce4-indicator-plugin:2603): Gtk-CRITICAL **: IA__gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed
```

---

### Post by Toz on 2012-05-08
> xrandr: cannot find output "--HDMI1"
Does your xrandr command work?

Other than that, there doesn't appear to be anything in your log file that would be delaying the startup. I would suggest temporarily disabling the 3 startup commands and the startup of dropbox to see if they are causing the delay. Disable them all, then enable them one at a time.

Also, maybe try creating a new test account to see if the delay occurs in a pristine login.

---

### Post by coleman_ian on 2012-05-08
I tried disabling all startup options (not just the ones I added) but no success.
I created a new user, and they log in just fine.

I have found another thread which is describing this same issue, I will be posting in that from here on in as it has partially solved my problem.

The issue is to do with accounts-daemon

Follow from here
[http://ubuntuforums.org/showthread.php?p=11918449#post11918449](http://ubuntuforums.org/showthread.php?p=11918449#post11918449)

Thanks for the help Toz.

---

