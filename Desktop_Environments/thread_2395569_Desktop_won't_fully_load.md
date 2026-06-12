---
title: "Desktop won't fully load"
date: 2018-07-03
forum: Desktop Environments
---

### Post by ajgringo619 on 2018-07-03
Not sure what happened, but after my last reboot (no packages have been updated since the last reboot) my desktop won't fully load. I get the background and mouse pointer, but nothing else; right-clicks do not bring up the menu. I can hit [CTRL]-[ALT]-[F1] to bring up a console to check the logs, but nothing seems out of place. When hit [CTRL]-[ATL]-[F7] to bring up the GUI again, my desktop has magically returned.

Any ideas? This system is a recently-loaded clean installation (dual-boot with Windows 10).

---

### Post by Frogs Hair on 2018-07-03
Please post the Ubuntu version in use.

---

### Post by ajgringo619 on 2018-07-03
Sorry, should have indicated that from the beginning...

XUbuntu 18.04 64bit / Linux 4.15.0-24-generic

---

### Post by ajgringo619 on 2018-07-04
OK, saw this after another test (logging off then back on this time); again I was able to get my desktop back after CTRL-ALT-F1 then CTL-ALT-F7:

```
Jul  3 22:02:58 DSS-Ubuntu xdg-desktop-por[2998]: Error getting permissions: GDBus.Error:org.freedesktop.portal.Error.NotFound: No entry for inhibit
Jul  3 22:02:58 DSS-Ubuntu xdg-desktop-por[2998]: Backend call failed: GDBus.Error:org.freedesktop.portal.Error.Failed: Inhibiting other than idle not supported
Jul  3 22:03:13 DSS-Ubuntu xfce4-notifyd[1589]: xfce4-notifyd: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
Jul  3 22:03:13 DSS-Ubuntu at-spi-bus-launcher[1505]: XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
Jul  3 22:03:13 DSS-Ubuntu at-spi-bus-launcher[1505]:       after 16633 requests (16633 known processed) with 0 events remaining.
Jul  3 22:03:13 DSS-Ubuntu systemd[1344]: xfce4-notifyd.service: Main process exited, code=exited, status=1/FAILURE
Jul  3 22:03:13 DSS-Ubuntu systemd[1344]: xfce4-notifyd.service: Failed with result 'exit-code'.
Jul  3 22:03:13 DSS-Ubuntu [3016]: xdg-desktop-portal-gtk: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
Jul  3 22:03:13 DSS-Ubuntu systemd[1344]: xdg-desktop-portal-gtk.service: Main process exited, code=exited, status=1/FAILURE
Jul  3 22:03:13 DSS-Ubuntu systemd[1344]: xdg-desktop-portal-gtk.service: Failed with result 'exit-code'.
Jul  3 22:03:13 DSS-Ubuntu kernel: [17287.995226] nvidia-modeset: Freed GPU:0 (GPU-a8d5ead9-23e5-c3e5-b491-96b50bb2ce16) @ PCI:0000:01:00.0
Jul  3 22:03:13 DSS-Ubuntu nvidia-persistenced: Received signal 15
Jul  3 22:03:13 DSS-Ubuntu nvidia-persistenced: Socket closed.
Jul  3 22:03:13 DSS-Ubuntu systemd[1]: Stopping NVIDIA Persistence Daemon...
Jul  3 22:03:13 DSS-Ubuntu nvidia-persistenced: PID file unlocked.
Jul  3 22:03:13 DSS-Ubuntu nvidia-persistenced: PID file closed.
Jul  3 22:03:13 DSS-Ubuntu nvidia-persistenced: The daemon no longer has permission to remove its runtime data directory /var/run/nvidia-persistenced
Jul  3 22:03:13 DSS-Ubuntu nvidia-persistenced: Shutdown (1143)
Jul  3 22:03:13 DSS-Ubuntu systemd[1]: Stopped NVIDIA Persistence Daemon.
Jul  3 22:03:13 DSS-Ubuntu systemd[1]: Starting NVIDIA Persistence Daemon...
Jul  3 22:03:13 DSS-Ubuntu nvidia-persistenced: Verbose syslog connection opened
Jul  3 22:03:13 DSS-Ubuntu nvidia-persistenced: Now running with user ID 121 and group ID 128
Jul  3 22:03:13 DSS-Ubuntu nvidia-persistenced: Started (4866)
Jul  3 22:03:13 DSS-Ubuntu systemd[1]: Started NVIDIA Persistence Daemon.
Jul  3 22:03:14 DSS-Ubuntu kernel: [17288.274833] resource sanity check: requesting [mem 0x000c0000-0x000fffff], which spans more than PCI Bus 0000:00 [mem 0x000c0000-0x000dffff window]
Jul  3 22:03:14 DSS-Ubuntu kernel: [17288.275294] caller os_map_kernel_space.part.7+0xda/0x120 [nvidia] mapping multiple BARs
Jul  3 22:03:14 DSS-Ubuntu nvidia-persistenced: device 0000:01:00.0 - registered
Jul  3 22:03:14 DSS-Ubuntu nvidia-persistenced: Local RPC service initialized
Jul  3 22:03:14 DSS-Ubuntu kernel: [17288.577524] nvidia-modeset: Allocated GPU:0 (GPU-a8d5ead9-23e5-c3e5-b491-96b50bb2ce16) @ PCI:0000:01:00.0
Jul  3 22:03:14 DSS-Ubuntu acpid: client 1126[0:0] has disconnected
Jul  3 22:03:14 DSS-Ubuntu acpid: client connected from 4860[0:0]
Jul  3 22:03:14 DSS-Ubuntu acpid: 1 client rule loaded
Jul  3 22:03:15 DSS-Ubuntu systemd[1]: Created slice User Slice of lightdm.
Jul  3 22:03:15 DSS-Ubuntu systemd[1]: Starting User Manager for UID 110...
Jul  3 22:03:15 DSS-Ubuntu systemd[1]: Started Session c4 of user lightdm.
Jul  3 22:03:15 DSS-Ubuntu systemd[4896]: Reached target Paths.
Jul  3 22:03:15 DSS-Ubuntu systemd[4896]: Starting D-Bus User Message Bus Socket.
Jul  3 22:03:15 DSS-Ubuntu systemd[4896]: Listening on GnuPG cryptographic agent and passphrase cache (restricted).
Jul  3 22:03:15 DSS-Ubuntu systemd[4896]: Reached target Timers.
Jul  3 22:03:15 DSS-Ubuntu systemd[4896]: Listening on GnuPG cryptographic agent and passphrase cache (access for web browsers).
Jul  3 22:03:15 DSS-Ubuntu systemd[4896]: Listening on GnuPG cryptographic agent (ssh-agent emulation).
Jul  3 22:03:15 DSS-Ubuntu systemd[4896]: Listening on GnuPG network certificate management daemon.
Jul  3 22:03:15 DSS-Ubuntu systemd[4896]: Listening on GnuPG cryptographic agent and passphrase cache.
Jul  3 22:03:15 DSS-Ubuntu systemd[4896]: Listening on D-Bus User Message Bus Socket.
Jul  3 22:03:15 DSS-Ubuntu systemd[4896]: Reached target Sockets.
Jul  3 22:03:15 DSS-Ubuntu systemd[4896]: Reached target Basic System.
Jul  3 22:03:15 DSS-Ubuntu systemd[4896]: Reached target Default.
Jul  3 22:03:15 DSS-Ubuntu systemd[4896]: Startup finished in 44ms.
Jul  3 22:03:15 DSS-Ubuntu systemd[1]: Started User Manager for UID 110.
Jul  3 22:03:15 DSS-Ubuntu systemd[4896]: Started D-Bus User Message Bus.
Jul  3 22:03:15 DSS-Ubuntu dbus-daemon[4917]: [session uid=110 pid=4917] AppArmor D-Bus mediation is enabled
Jul  3 22:03:15 DSS-Ubuntu dbus-daemon[4917]: [session uid=110 pid=4917] Activating via systemd: service name='org.a11y.Bus' unit='at-spi-dbus-bus.service' requested by ':1.1' (uid=110 pid=4915 comm="/usr/sbin/lightdm-gtk-greeter " label="unconfined")
Jul  3 22:03:15 DSS-Ubuntu systemd[4896]: Starting Accessibility services bus...
Jul  3 22:03:15 DSS-Ubuntu dbus-daemon[4917]: [session uid=110 pid=4917] Activating via systemd: service name='org.gtk.vfs.Daemon' unit='gvfs-daemon.service' requested by ':1.2' (uid=110 pid=4918 comm="/usr/lib/at-spi2-core/at-spi-bus-launcher " label="unconfined")
Jul  3 22:03:15 DSS-Ubuntu systemd[4896]: Starting Virtual filesystem service...
Jul  3 22:03:15 DSS-Ubuntu dbus-daemon[4917]: [session uid=110 pid=4917] Successfully activated service 'org.gtk.vfs.Daemon'
Jul  3 22:03:15 DSS-Ubuntu systemd[4896]: Started Virtual filesystem service.
Jul  3 22:03:15 DSS-Ubuntu dbus-daemon[4917]: [session uid=110 pid=4917] Successfully activated service 'org.a11y.Bus'
Jul  3 22:03:15 DSS-Ubuntu systemd[4896]: Started Accessibility services bus.
Jul  3 22:03:15 DSS-Ubuntu at-spi-bus-launcher[4918]: dbus-daemon[4935]: Activating service name='org.a11y.atspi.Registry' requested by ':1.0' (uid=110 pid=4915 comm="/usr/sbin/lightdm-gtk-greeter " label="unconfined")
Jul  3 22:03:15 DSS-Ubuntu at-spi-bus-launcher[4918]: dbus-daemon[4935]: Successfully activated service 'org.a11y.atspi.Registry'
Jul  3 22:03:15 DSS-Ubuntu at-spi-bus-launcher[4918]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Jul  3 22:03:25 DSS-Ubuntu systemd[1]: session-c4.scope: Killing process 4875 (lightdm) with signal SIGTERM.
Jul  3 22:03:25 DSS-Ubuntu systemd[1]: session-c4.scope: Killing process 4911 (gnome-keyring-d) with signal SIGTERM.
Jul  3 22:03:25 DSS-Ubuntu systemd[1]: session-c4.scope: Killing process 4914 (lightdm-greeter) with signal SIGTERM.
Jul  3 22:03:25 DSS-Ubuntu systemd[1]: session-c4.scope: Killing process 4915 (lightdm-gtk-gre) with signal SIGTERM.
Jul  3 22:03:25 DSS-Ubuntu systemd[1]: Stopping Session c4 of user lightdm.
Jul  3 22:03:25 DSS-Ubuntu systemd[1]: Stopped Session c4 of user lightdm.
Jul  3 22:03:25 DSS-Ubuntu systemd[1]: Stopping User Manager for UID 110...
Jul  3 22:03:25 DSS-Ubuntu systemd[4896]: Stopping Virtual filesystem service...
Jul  3 22:03:25 DSS-Ubuntu systemd[4896]: Stopping Accessibility services bus...
Jul  3 22:03:25 DSS-Ubuntu systemd[4896]: Stopping D-Bus User Message Bus...
Jul  3 22:03:25 DSS-Ubuntu systemd[4896]: Stopped target Default.
Jul  3 22:03:25 DSS-Ubuntu systemd[4896]: Stopped Accessibility services bus.
Jul  3 22:03:25 DSS-Ubuntu systemd[4896]: Stopped D-Bus User Message Bus.
Jul  3 22:03:25 DSS-Ubuntu systemd[1]: Started Session c5 of user summersd.
Jul  3 22:03:25 DSS-Ubuntu systemd[4896]: Stopped Virtual filesystem service.
Jul  3 22:03:25 DSS-Ubuntu systemd[4896]: Stopped target Basic System.
Jul  3 22:03:25 DSS-Ubuntu systemd[4896]: Stopped target Paths.
Jul  3 22:03:25 DSS-Ubuntu systemd[4896]: Stopped target Sockets.
Jul  3 22:03:25 DSS-Ubuntu systemd[4896]: Closed GnuPG cryptographic agent and passphrase cache (access for web browsers).
Jul  3 22:03:25 DSS-Ubuntu systemd[4896]: Closed GnuPG cryptographic agent and passphrase cache.
Jul  3 22:03:25 DSS-Ubuntu systemd[4896]: Closed GnuPG network certificate management daemon.
Jul  3 22:03:25 DSS-Ubuntu systemd[4896]: Closed GnuPG cryptographic agent and passphrase cache (restricted).
Jul  3 22:03:25 DSS-Ubuntu systemd[4896]: Closed GnuPG cryptographic agent (ssh-agent emulation).
Jul  3 22:03:25 DSS-Ubuntu systemd[4896]: Stopped target Timers.
Jul  3 22:03:25 DSS-Ubuntu systemd[4896]: Closed D-Bus User Message Bus Socket.
Jul  3 22:03:25 DSS-Ubuntu systemd[4896]: Reached target Shutdown.
Jul  3 22:03:25 DSS-Ubuntu systemd[4896]: Starting Exit the Session...
Jul  3 22:03:25 DSS-Ubuntu systemd[4896]: Received SIGRTMIN+24 from PID 4974 (kill).
Jul  3 22:03:25 DSS-Ubuntu systemd[1]: Stopped User Manager for UID 110.
Jul  3 22:03:25 DSS-Ubuntu systemd[1]: Removed slice User Slice of lightdm.
Jul  3 22:03:25 DSS-Ubuntu at-spi-bus-launcher[1505]: dbus-daemon[1532]: Activating service name='org.a11y.atspi.Registry' requested by ':1.26' (uid=1000 pid=5112 comm="xfce4-power-manager " label="unconfined")
Jul  3 22:03:25 DSS-Ubuntu at-spi-bus-launcher[1505]: dbus-daemon[1532]: Successfully activated service 'org.a11y.atspi.Registry'
Jul  3 22:03:25 DSS-Ubuntu at-spi-bus-launcher[1505]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Jul  3 22:03:25 DSS-Ubuntu spice-vdagent[5119]: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
Jul  3 22:03:25 DSS-Ubuntu dbus-daemon[1377]: [session uid=1000 pid=1377] Activating via systemd: service name='org.freedesktop.Notifications' unit='xfce4-notifyd.service' requested by ':1.178' (uid=1000 pid=5112 comm="xfce4-power-manager " label="unconfined")
Jul  3 22:03:25 DSS-Ubuntu systemd[1344]: Starting XFCE notifications service...
Jul  3 22:03:25 DSS-Ubuntu dbus-daemon[1377]: [session uid=1000 pid=1377] Successfully activated service 'org.freedesktop.Notifications'
Jul  3 22:03:25 DSS-Ubuntu systemd[1344]: Started XFCE notifications service.
Jul  3 22:03:25 DSS-Ubuntu dbus-daemon[1377]: [session uid=1000 pid=1377] Activating via systemd: service name='org.gnome.evolution.dataserver.Calendar7' unit='evolution-calendar-factory.service' requested by ':1.192' (uid=1000 pid=5117 comm="/usr/lib/evolution/evolution-alarm-notify " label="unconfined")
Jul  3 22:03:25 DSS-Ubuntu systemd[1344]: Starting Evolution calendar service...
Jul  3 22:03:26 DSS-Ubuntu dbus-daemon[1377]: [session uid=1000 pid=1377] Successfully activated service 'org.gnome.evolution.dataserver.Calendar7'
Jul  3 22:03:26 DSS-Ubuntu systemd[1344]: Started Evolution calendar service.
Jul  3 22:03:26 DSS-Ubuntu evolution-sourc[1688]: Remote error from secret service: org.freedesktop.DBus.Error.ServiceUnknown: The name :1.6 was not provided by any .service files
Jul  3 22:03:27 DSS-Ubuntu evolution-sourc[1688]: message repeated 7 times: [ Remote error from secret service: org.freedesktop.DBus.Error.ServiceUnknown: The name :1.6 was not provided by any .service files]
Jul  3 22:04:26 DSS-Ubuntu /hp-systray: hp-systray(qt5)[5115]: error:  No system tray detected on this system.  Unable to start, exiting.
Jul  3 22:04:42 DSS-Ubuntu kernel: [17376.852873] [UFW BLOCK] IN=enp5s0 OUT= MAC=01:00:5e:00:00:01:38:70:0c:ca:83:85:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=6133 PROTO=2 
Jul  3 22:05:15 DSS-Ubuntu acpid: client 4860[0:0] has disconnected
Jul  3 22:05:16 DSS-Ubuntu acpid: client connected from 4860[0:0]
Jul  3 22:05:16 DSS-Ubuntu acpid: 1 client rule loaded
```

I let the system sit for about 10 minutes before forcing it to come back up.

---

