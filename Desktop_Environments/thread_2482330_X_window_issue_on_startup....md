---
title: "X window issue on startup..."
date: 2022-12-28
forum: Desktop Environments
---

### Post by dbee on 2022-12-28
Whenever i startup my laptop, i see a misconfigured homescreen. I have to login to tty3 and restart gnome in order to get it back working.

Pls. see screen attached...

```

localhost: uname -a
Linux dara-HP-Stream-Laptop-11-y0XX 5.15.0-56-generic #62-Ubuntu SMP Tue Nov 22 19:54:14 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

```

```

localhost: cat /etc/X11/default-display-manager
/usr/sbin/lightdm

```

I know I'm using X, not wayland but apart from that I can't find anything in /proc to give more details. 

I've reinstalled gnome, no luck there...

---

### Post by Holger_Gehrke on 2022-12-29
That button in the lower left corner looks a lot like the XFCE menu button. Could it be that you have XFCE installed in addition to Gnome and the system is starting up with that ?

Holger

---

### Post by tea for one on 2022-12-29
> **dbee said:**
> ```

localhost: cat /etc/X11/default-display-manager
/usr/sbin/lightdm

```
Gnome requires gdm3 display manager.
lightdm is installed with Xubuntu.

---

### Post by dbee on 2023-01-03
Thanks, guys. More info.

I wrote gnome_restrart to basically - restart gnome and reset the display.

```

[1] 4321
localhost: gnome_restart
libmutter-Message: 12:39:52.759: Running GNOME Shell (using mutter 42.5) as a X11 window and compositing manager

** (gnome-shell:4321): WARNING **: 12:39:53.194: ATK Bridge is disabled but a11y has already been enabled.

** (gnome-shell:4321): WARNING **: 12:39:53.932: Unable to register authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for the given subject
GNOME Shell-Message: 12:39:53.933: Failed to register AuthenticationAgent
GNOME Shell-Message: 12:39:53.935: Telepathy is not available, chat integration will be disabled.
GNOME Shell-Message: 12:39:53.997: Failed to create file /run/user/1000/gnome-shell-disable-extensions: Error opening file “/run/user/1000/gnome-shell-disable-extensions”: File exists
current session already has an ibus-daemon.

(gnome-shell:4321): libmutter-WARNING **: 12:39:54.260: Lost or failed to acquire name org.gnome.Mutter.ScreenCast

(gnome-shell:4321): libmutter-WARNING **: 12:39:54.260: Lost or failed to acquire name org.gnome.Mutter.RemoteDesktop
GNOME Shell-Message: 12:39:54.471: Error looking up permission: GDBus.Error:org.freedesktop.portal.Error.NotFound: No entry for geolocation
GNOME Shell-Message: 12:39:56.408: GNOME Shell started at Tue Jan 03 2023 12:39:53 GMT+0000 (GMT)
GNOME Shell-Message: 12:39:56.409: Registering session with GDM
GNOME Shell-Message: 12:39:56.416: Error registering session with GDM: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.DisplayManager was not provided by any .service files

```

---

### Post by dbee on 2023-01-10
Right. Thanks.

So, what should I do to fix my GUI?

---

### Post by dbee on 2023-01-19
i've asked on StackOverflow and they've sent me to AskUbuntu, guys.

If someone could point me in the right direction, that'd be great! A link, perhaps?

---

