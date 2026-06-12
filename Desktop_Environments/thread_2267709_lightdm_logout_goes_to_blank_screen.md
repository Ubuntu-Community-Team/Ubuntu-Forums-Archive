---
title: "lightdm logout goes to blank screen"
date: 2015-03-03
forum: Desktop Environments
---

### Post by peridian on 2015-03-03
Hi,

I have a Ubuntu 14.04.1 install where I removed the Unity desktop and replaced with lightdm.  I can shutdown/reboot just fine, but when I try logout term #1 goes to a blank screen with the cursor blinking away.

Hunting around on the web shows problems with restarting the X service exist, but most of the solutions appear to be for the KDE desktop, not lightdm.

Does anybody know how to fix this?

Regards,
Rob.

---

### Post by ajgreeny on 2015-03-03
I m wondering what DE or window-manager you are now using, as lightdm is not able to show anything on its own, as far as I'm aware.

You have tagged this as Lubuntu; what OS exactly have you installed and why did you remove unity?

---

### Post by peridian on 2015-03-03
Sorry, it is Ubuntu not Lubuntu, I will try to change that.

Unity caused me nothing but headaches.  This device is a low-powered laptop, and Unity kept causing the desktop to freeze and hang, as though it had a memory leak.  So I removed it in favour of lubuntu/lightdm which I was already using on an actual Lubuntu install on a Raspberry Pi without issues.

I've searched the logs, and found some errors that coincide with when I hit logout.  Don't know if that's just coincidence/normal or indicative of the problem:

/var/log/syslog

```

Mar  3 19:50:27 hostname NetworkManager[1030]: <warn> error requesting auth for org.freedesktop.NetworkManager.enable-disable-wifi: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.27': no such name
Mar  3 19:50:27 hostname NetworkManager[1030]: <warn> error requesting auth for org.freedesktop.NetworkManager.enable-disable-wwan: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.27': no such name
Mar  3 19:50:27 hostname NetworkManager[1030]: <warn> error requesting auth for org.freedesktop.NetworkManager.enable-disable-wimax: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.27': no such name
Mar  3 19:50:27 hostname NetworkManager[1030]: <warn> error requesting auth for org.freedesktop.NetworkManager.network-control: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.27': no such name
Mar  3 19:50:27 hostname NetworkManager[1030]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.27': no such name
Mar  3 19:50:27 hostname NetworkManager[1030]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.27': no such name
Mar  3 19:50:27 hostname NetworkManager[1030]: <warn> error requesting auth for org.freedesktop.NetworkManager.settings.modify.system: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.27': no such name
Mar  3 19:50:27 hostname NetworkManager[1030]: <warn> error requesting auth for org.freedesktop.NetworkManager.settings.modify.own: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.27': no such name
Mar  3 19:50:27 hostname NetworkManager[1030]: <warn> error requesting auth for org.freedesktop.NetworkManager.settings.modify.hostname: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.27': no such name
Mar  3 19:50:29 hostname acpid: client 1384[0:0] has disconnected

```

/var/log/auth.log

```

Mar  3 19:50:26 hostname polkitd(authority=local): Unregistered Authentication Agent for unix-session:c2 (system bus name :1.24, object path /org/freedesktop/PolicyKit1/AuthenticationAgent, locale en_GB.UTF-8) (disconnected from bus)
Mar  3 19:46:34 hostname gnome-keyring-daemon[1545]: message repeated 2 times: [ couldn't set environment variable in session: The name org.gnome.SessionManager was not provided by any .service files]
Mar  3 19:50:26 hostname gnome-keyring-daemon[1545]: g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
Mar  3 19:50:26 hostname lightdm: pam_unix(lightdm:session): session closed for user local-admin

```

Regards,
Rob.

---

### Post by ajgreeny on 2015-03-04
Sorry, but I'm still confused about what OS you are using!

You say "Sorry, it is Ubuntu not Lubuntu, I will try to change that." but then you go on to say "So I removed it in favour of lubuntu/lightdm"
So which is it on your machine and which DE is it using now?

Have you perhaps just removed the **ubuntu-desktop** package and replaced that with** lubuntu-desktop** package?

---

### Post by peridian on 2015-03-04
Correct, the change was to the desktop packages only, the install is still Ubuntu.  I can't seem to change the thread indicator from lubuntu to ubuntu, don't know if that's even possible.

Rob.

---

### Post by ajgreeny on 2015-03-05
If you simply removed the ubuntu-desktop package it will not have removed all of the applications that were installed, I'm afraid, as ubuntu-desktop is just a meta-package, meaning it does not add anything itself but simply has dependencies of all the applications of the standard ubuntu install including unity, nautilus the file-manager, gnome-terminal etc etc, so you will possibly still have a lot of the original applications from your ubuntu in the OS.

---

