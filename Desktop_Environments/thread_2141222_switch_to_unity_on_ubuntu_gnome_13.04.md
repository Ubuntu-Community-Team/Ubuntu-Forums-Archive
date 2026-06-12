---
title: "switch to unity on ubuntu gnome 13.04"
date: 2013-05-02
forum: Desktop Environments
---

### Post by galgalesh on 2013-05-02
Hi

I have been using ubuntu gnome 13.04 for a few days, but I want to switch to unity. I'm in the middle of Africa with a bad internet connection so I'd rather not have to download the ubuntu iso.

Here's what I tried so far:

[B]Install ubuntu-desktop
[/B]This gave me unity back, but without the correct settings (icons, themes, startup wallpaper, ...)

[B]unity --reset-icons
[/B]Gave a lot of errors, had to kill it.

[B]dconf reset -f /org/compiz
[/B]Gave a lot of errors, had to kill it.

**The errors:**
```

WARN  2013-05-02 08:59:15 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window71303173
WARN  2013-05-02 08:59:15 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window71303173
WARN  2013-05-02 08:59:15 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window71303173
WARN  2013-05-02 08:59:15 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window71303173
WARN  2013-05-02 08:59:15 unity.glib.dbus.proxy GLibDBusProxy.cpp:418 Calling method "CanHibernate" on object path: "/org/freedesktop/login1" failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.login1 was not provided by any .service files
ERROR 2013-05-02 08:59:15 unity.session.gnome GnomeSessionManager.cpp:334 logind CanHibernate call failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.login1 was not provided by any .service files
WARN  2013-05-02 08:59:15 unity.glib.dbus.proxy GLibDBusProxy.cpp:418 Calling method "CanSuspend" on object path: "/org/freedesktop/login1" failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.login1 was not provided by any .service files
ERROR 2013-05-02 08:59:15 unity.session.gnome GnomeSessionManager.cpp:334 logind CanSuspend call failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.login1 was not provided by any .service files
WARN  2013-05-02 08:59:15 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window71303173
WARN  2013-05-02 08:59:15 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window71303173
WARN  2013-05-02 08:59:15 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window71303173

```

What I would like is to have the default ubuntu/unity experience as if i'd installed it with the ubuntu iso. Anyone have any suggestions?

---

### Post by grahammechanical on 2013-05-02
You are asking a lot. It is one thing to install Gnome 3 Shell on Ubuntu. It is another thing to convert Ubuntu Gnome to Ubuntu. May I suggest that you install Synaptic Package Manager and then search for Ubuntu. Do you have ubuntu-wallpapers-raring installed? Or ubuntu-settings installed. Then there is branding-ubuntu; ubuntu-mono; ubuntu-artwork; plymouth-theme-ubuntu-logo; ubuntu-minimal; plymouth-theme-ubuntu-text; ttf-ubuntu-font-family;unity-webapps-common; ubuntu-system-service; notify-osd-icons; light-themes.

Those are some of the packages that I have on my Raring Ringtail. I have no idea if they are present on Ubuntu Gnome 13.04. But you will need them.

Regards.

---

### Post by galgalesh on 2013-05-03
Thank you for your reply. I will look into those packages.

I understand I'm asking a lot so let's narrow the search a bit. There are two things that are bugging me a lot and that I would like to change:


[LIST=1]
[*]The startup splash screen. I thought it would become the ubuntu one when I switched to the lightdm but is is still the gnome one.
[*]The "turn your computer off" dialog. I thought it was revamped for ubuntu 13.04 but I'm still seeing the "old" one.
[/LIST]

---

### Post by markbl on 2013-05-03
Actually, I am not sure of this at all but an "apt-get install ubuntu-desktop ubuntu-settings" may get you close? Let me know how you go.

---

### Post by galgalesh on 2013-05-03
Hi Markbl

Thanks for your help. I already did that. Installing ubuntu-desktop gave me unity back but some settings are still wrong. ubuntu-settings installs automatically with ubuntu-desktop but it seems that is does not include(or change) all settings.

@grahammechanical:
All those packages are automatically installed with the ubuntu-dekstop package.

---

### Post by markbl on 2013-05-03
Sorry, I didn't realise ubuntu-settings was in ubuntu-desktop.

FYI, I installed ubuntu-gnome-default-settings at one point and lost all my nice ubuntu fonts, theme, etc but a "aptitude reinstall ubuntu-settings" restored it for me.

---

### Post by galgalesh on 2013-05-03
UPDATE:

What I did so far:

**Got icons and theme back with gnome tweak tool:**
Icon theme: ubuntu-mono-dark
gtk+ theme: Ambiance
Current theme: Ambiance

**Got boot splash screen back by removing plymouth gnome theme:**
```
sudo apt-get remove plymouth-theme-ubuntu-gnome-logo
sudo apt-get remove plymouth-theme-ubuntu-gnome-text
```

After doing this, I got the fancy "goodbye" screen back but don't ask me why. As I understand it plymouth is the graphical boot animation so I have no idea why this would change the "goodbye" screen.

---

