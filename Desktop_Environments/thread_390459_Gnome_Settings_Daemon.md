---
title: "Gnome Settings Daemon"
date: 2007-03-22
forum: Desktop Environments
---

### Post by sjb05004 on 2007-03-22
I recently got an error after making small changes to my settings.  I installed gnome and e17.  I was gonna try enlightened gnome and used these commands.

sudo cp /usr/share/gnome/default.session ~/.gnome2/session

sudo gedit ~/.gnome2/session

1,RestartCommand=gnome-wm --sm-client-id default1

1,RestartCommand=gnome-wm --default-wm enlightenment --sm-client-id default1


'After these commands tried gnome desktop and got this error:

There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Unable to determine the address of the message bus (try 'man dbus-launch' and 'man dbus-daemon' for help)

GNOME will still try to restart the Settings Daemon next time you log in.'


I tried to manually run gnome-settings-daemon and got this:

(gnome-settings-daemon:5586): GSwitchIt-WARNING **: Unable to connect to dbus: Unable to determine the address of the message bus (try 'man dbus-launch' and 'man dbus-daemon' for help)

** (gnome-settings-daemon:5586): CRITICAL **: dbus_g_connection_register_g_object: assertion `connection != NULL' failed

** (gnome-settings-daemon:5586): CRITICAL **: dbus_g_proxy_new_for_name: assertion `connection != NULL' failed

** (gnome-settings-daemon:5586): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (bug-buddy:5592): WARNING **: Couldn't load icon for Open Folder


Not sure what to do anymore, other than clean install.  Any ideas or help would be greatly appreciated. Thanks.



 

I've tried all I can think of.  Any help will be appreciated.

---

### Post by tcrroadie on 2007-03-22
Are you saying since you created a custom gnome session file for your normal user, you are having problems when Gnome is started?  

If so, just try deleting your personal gnome2/session file. 
```

rm ~/.gnome2/session
```

Then reboot your machine and login to Gnome.  A new session file will be created after your restart Gnome as your normal user.

---

### Post by ernstblaauw on 2007-03-22
I also just got this error. I did not change any settings. I added a DVD-RW to my system, but I don't think it has anything to do with that. Is it possible a recent update causes this problem?

Is it possible I do not have a session file? I cannot find it and I also get an error message when I insert that command.

---

### Post by ayoli on 2007-03-22
> **ernstblaauw said:**
> I also just got this error. I did not change any settings. I added a DVD-RW to my system, but I don't think it has anything to do with that. Is it possible a recent update causes this problem?

Is it possible I do not have a session file? I cannot find it and I also get an error message when I insert that command.
you do not have a session file in ~/.gnome2/ if you don't use save session functionality

---

