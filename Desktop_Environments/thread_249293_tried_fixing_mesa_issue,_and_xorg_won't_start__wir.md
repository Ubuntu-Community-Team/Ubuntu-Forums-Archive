---
title: "tried fixing mesa issue, and xorg won't start / wireless doesn't work"
date: 2006-09-02
forum: Desktop Environments
---

### Post by Jacks0n on 2006-09-02
Hi, I tried [this]("http://www.ubuntuforums.org/showthread.php?t=143283") Howto, and..

I removed "linux-restricted-modules-$(uname -r)", the other wasn't ever there. Changed the xorg driver from mesa to Ati. And rebooted. then xorg wouldn't start. I'm using the xorg backup, but now my wireless won't work. it isn't even recognized. I didn't do anything else at the time, terminal and firefox were the only programs open.

this is the log for xsession:

```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "jackson"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/jackson-laptop:/tmp/.ICE-unix/5007
esd: Esound sound daemon already running or stale UNIX socket
/tmp/.esd-1000/socket
This socket already exists indicating esd is already running.
Exiting...
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

(gnome-panel:5085): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

(gnome-panel:5085): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -9 and height 24
libmikmod.so.2: cannot open shared object file: No such file or directory
Message: device: default
(network-admin:6152): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
W: Unable to locate package stop-bootlogd
E: No packages found
substr outside of string at /usr/lib/bum/bumlib.pm line 287.
Use of uninitialized value in split at /usr/lib/bum/bumlib.pm line 289.
Use of uninitialized value in substitution (s///) at /usr/lib/bum/bumlib.pm line 292.
Use of uninitialized value in string eq at /usr/lib/bum/bumlib.pm line 295.
eth1      Interface doesn't support scanning.

eth1: error fetching interface information: Device not found
eth1      No such device

eth1      Interface doesn't support scanning.

eth1: error fetching interface information: Device not found
eth1      No such device

eth1      Interface doesn't support scanning.

eth1: error fetching interface information: Device not found
eth1      No such device

eth1      Interface doesn't support scanning.

eth1: error fetching interface information: Device not found
eth1      No such device

eth1      Interface doesn't support scanning.

eth1: error fetching interface information: Device not found
eth1      No such device

eth1      Interface doesn't support scanning.

eth1: error fetching interface information: Device not found
eth1      No such device

eth1      Interface doesn't support scanning.

eth1: error fetching interface information: Device not found
eth1      No such device

eth1      Interface doesn't support scanning.

eth1: error fetching interface information: Device not found
eth1      No such device

eth1      Interface doesn't support scanning.

eth1: error fetching interface information: Device not found
eth1      No such device

eth1      Interface doesn't support scanning.

eth1: error fetching interface information: Device not found
eth1      No such device

eth1      Interface doesn't support scanning.

eth1: error fetching interface information: Device not found
eth1      No such device

eth1      Interface doesn't support scanning.

eth1: error fetching interface information: Device not found
eth1      No such device

eth1      Interface doesn't support scanning.

eth1: error fetching interface information: Device not found
eth1      No such device

Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; No such device.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
eth1      Interface doesn't support scanning.

eth1: error fetching interface information: Device not found
eth1      No such device

eth1      Interface doesn't support scanning.

eth1: error fetching interface information: Device not found
eth1      No such device

Bind socket to interface: No such device
eth1      Interface doesn't support scanning.

eth1: error fetching interface information: Device not found
eth1: error fetching interface information: Device not found
eth1      No such device

eth1      Interface doesn't support scanning.

eth1: error fetching interface information: Device not found
eth1      No such device

eth1      Interface doesn't support scanning.

eth1: error fetching interface information: Device not found
eth1      No such device

eth1      Interface doesn't support scanning.

eth1: error fetching interface information: Device not found
eth1      No such device

eth1      Interface doesn't support scanning.

eth1: error fetching interface information: Device not found
eth1      No such device

eth1      Interface doesn't support scanning.

eth1: error fetching interface information: Device not found
eth1      No such device

eth1      Interface doesn't support scanning.

eth1: error fetching interface information: Device not found
eth1      No such device

Stale pid file.  Removing
Message: alsa mixer timed out

** (update-notifier:5098): WARNING **: no cdrom: disk


** (update-notifier:5098): WARNING **: no cdrom: disk

closing

```

so.. 1. how do I get 3d hardware acceleration working?
and 2. how do I fix the wireless?

I really have no idea what went wrong, it's a relativly new install.

-thanks, jackson

---

