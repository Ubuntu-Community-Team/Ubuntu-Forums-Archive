---
title: "error that forces me to logout thus I cannot report"
date: 2022-11-23
forum: Desktop Environments
---

### Post by Claus7 on 2022-11-23
Hello,

there is sometime now that when I do something on screen, suddenly a white screen appears with a black sad face prompting me to lot out from session, since something went wrong and cannot recover. This has happened in different machines using different versions of ubuntu.

This is very annoying because I do not have any chance of saving my work at that time. When this happens I do something with the open windows: transferring a file from one folder to the other using drag and drop or trying to maximize a window e.t.c..

The thing is that I have the ability to check all open windows and applications that were open by pressing super+tab under ubuntu flashback. One of these windows is the prompt message for reporting the bug. The moment I release the super+tab so as for that message to come in front, the unhappy message takes its place. As a result I'm losing the ability to report the bug with all the necessary information.
Every window seems to be functional and I can see its contents. What I cannot do is to get rid of this unhappy face message that takes all the screen.

Any information on how I could report this, would be very welcome.
Here is the Logs file, while this happened:
> 
22:47:01 dbus-daemon: [session uid=1000 pid=73258] Successfully activated service 'org.gnome.Logs'
22:46:58 update-manager: Theme parsing error: gtk.css:15:25: '0' is not a valid color name
22:46:56 list-oem-metapa: 
Reading state information... 0% 

Reading state information... 0%

Reading state information... Done
22:46:55 pkexec: inno: Executing command [USER=root] [TTY=unknown] [CWD=/home/inno] [COMMAND=/usr/lib/update-notifier/package-system-locked]
22:46:53 livepatch-notif: Theme parsing error: gtk.css:15:25: '0' is not a valid color name
22:46:53 systemd: Started Application launched by gnome-session-binary.
22:46:31 packagekitd: search-file transaction /18986_aabeddeb from uid 1000 finished with success after 450ms
22:46:26 systemd: geoclue.service: Deactivated successfully.
22:46:26 geoclue: Service not used for 60 seconds. Shutting down..
22:46:25 packagekitd: search-file transaction /18976_bddbeccb from uid 1000 finished with success after 705ms
22:46:22 systemd: systemd-hostnamed.service: Deactivated successfully.
22:46:21 packagekitd: search-file transaction /18970_eadabbbb from uid 1000 finished with success after 719ms
22:46:21 systemd: systemd-timedated.service: Deactivated successfully.
22:46:21 packagekitd: search-file transaction /18969_babcdaec from uid 1000 finished with success after 854ms
22:46:11 systemd: user-125.slice: Consumed 13.275s CPU time.
22:46:11 wireplumber: disconnected from pipewire
22:46:11 systemd: Stopping Multimedia Service Session Manager...
22:46:11 tracker-miner-f: OK
22:46:11 systemd: Stopped PipeWire PulseAudio.
22:46:11 tracker-miner-f: Owner of volume monitor org.gtk.vfs.AfcVolumeMonitor disconnected from the bus; removing drives/volumes/mounts
22:46:11 gvfsd: A connection to the bus can't be made
22:46:11 systemd: Stopping D-Bus User Message Bus...
22:46:11 packagekitd: search-file transaction /18953_cabcdeec from uid 1000 finished with success after 430ms
22:46:07 kernel: VMMR0InitVM: eflags=246 fKernelFeatures=0x0 (SUPKERNELFEATURES_SMAP=0)
22:46:07 kernel: vboxdrv: 0000000000000000 VBoxDDR0.r0
22:46:07 packagekitd: search-file transaction /18945_acbbdbed from uid 1000 finished with success after 716ms
22:46:05 gnome-software: Tried to set invalid release date: 2022
22:46:04 packagekitd: resolve transaction /18941_bddbbdae from uid 1000 finished with success after 346ms
22:46:03 gnome-software: Only 0 apps for recent list, hiding
22:46:01 polkitd: Unregistered Authentication Agent for unix-session:c3 (system bus name :1.464, object path /org/freedesktop/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8) (disconnected from bus)
22:46:01 systemd-logind: Removed session c3.
22:46:01 systemd: session-c3.scope: Consumed 5.145s CPU time.
22:46:01 systemd-logind: Session c3 logged out. Waiting for processes to exit.
22:46:01 gdm-session-wor: GLib-GObject: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
22:46:01 gnome-session-b: WARNING: Lost name on bus: org.gnome.SessionManager
22:46:01 gnome-shell: Connection to xwayland lost
22:46:01 VirtualBox: Theme parsing error: gtk.css:15:25: '0' is not a valid color name
22:46:01 packagekitd: refresh-cache transaction /18939_cbeacbed from uid 1000 finished with success after 5815ms
22:45:57 systemd: fprintd.service: Deactivated successfully.
22:45:55 dbus-daemon: [session uid=1000 pid=73258] Successfully activated service 'org.freedesktop.Tracker3.Miner.Extract'
22:45:55 systemd: Starting Tracker metadata extractor...
22:45:55 dbus-daemon: [session uid=1000 pid=73258] Activating via systemd: service name='org.freedesktop.Tracker3.Miner.Extract' unit='tracker-extract-3.service' requested by ':1.76' (uid=1000 pid=74015 comm="/usr/libexec/tracker-miner-fs-3" label="unconfined")
22:45:55 packagekitd: uid 1000 obtained auth for org.freedesktop.packagekit.system-sources-refresh
22:45:55 nemo-desktop: Ignoring thumbnailer with missing binary: 'freecad-thumbnailer'
22:45:55 gnome-software: disabled plugins: dpkg, dummy, repos, epiphany
22:45:54 systemd: Started Virtual filesystem metadata service.
22:45:54 dbus-daemon: [session uid=1000 pid=73258] Successfully activated service 'org.gtk.vfs.Metadata'
22:45:54 systemd: Starting Virtual filesystem metadata service...
22:45:54 dbus-daemon: [session uid=1000 pid=73258] Activating via systemd: service name='org.gtk.vfs.Metadata' unit='gvfs-metadata.service' requested by ':1.79' (uid=1000 pid=74032 comm="nemo-desktop" label="unconfined")
22:45:54 compiz: compiz (decor) - Warn: No default decoration found, placement will not be correct
22:45:54 systemd: Started Portal service.
22:45:54 dbus-daemon: [session uid=1000 pid=73258] Successfully activated service 'org.freedesktop.portal.Desktop'
22:45:54 systemd: Started Portal service (GTK/GNOME implementation).
22:45:54 dbus-daemon: [session uid=1000 pid=73258] Successfully activated service 'org.freedesktop.impl.portal.desktop.gtk'
22:45:54 xdg-desktop-por: Theme parsing error: gtk.css:15:25: '0' is not a valid color name
22:45:54 nemo-desktop: nemo-desktop: session is not cinnamon (checked XDG_SESSION_DESKTOP,DESKTOP_SESSION environment variables.) Applying default behavior
22:45:54 systemd: Starting Portal service (GTK/GNOME implementation)...
22:45:54 dbus-daemon: [session uid=1000 pid=73258] Activating via systemd: service name='org.freedesktop.impl.portal.desktop.gtk' unit='xdg-desktop-portal-gtk.service' requested by ':1.90' (uid=1000 pid=74134 comm="/usr/libexec/xdg-desktop-portal" label="unconfined")
22:45:54 rtkit-daemon: Supervising 12 threads of 6 processes of 2 users.
22:45:54 systemd: Started Portal service (GNOME implementation).
22:45:54 dbus-daemon: [session uid=1000 pid=73258] Successfully activated service 'org.freedesktop.impl.portal.desktop.gnome'
22:45:54 systemd: Starting Portal service (GNOME implementation)...
22:45:54 dbus-daemon: [session uid=1000 pid=73258] Activating via systemd: service name='org.freedesktop.impl.portal.desktop.gnome' unit='xdg-desktop-portal-gnome.service' requested by ':1.90' (uid=1000 pid=74134 comm="/usr/libexec/xdg-desktop-portal" label="unconfined")
22:45:54 systemd: Started flatpak document portal service.
22:45:54 dbus-daemon: [session uid=1000 pid=73258] Successfully activated service 'org.freedesktop.portal.Documents'
22:45:54 systemd: Started sandboxed app permission store.
22:45:54 dbus-daemon: [session uid=1000 pid=73258] Successfully activated service 'org.freedesktop.impl.portal.PermissionStore'
22:45:54 systemd: Starting sandboxed app permission store...
22:45:54 dbus-daemon: [session uid=1000 pid=73258] Activating via systemd: service name='org.freedesktop.impl.portal.PermissionStore' unit='xdg-permission-store.service' requested by ':1.91' (uid=1000 pid=74138 comm="/usr/libexec/xdg-document-portal" label="unconfined")
22:45:54 systemd: Starting flatpak document portal service...
22:45:54 dbus-daemon: [session uid=1000 pid=73258] Activating via systemd: service name='org.freedesktop.portal.Documents' unit='xdg-document-portal.service' requested by ':1.90' (uid=1000 pid=74134 comm="/usr/libexec/xdg-desktop-portal" label="unconfined")
22:45:54 systemd: Starting Portal service...
22:45:54 dbus-daemon: [session uid=1000 pid=73258] Activating via systemd: service name='org.freedesktop.portal.Desktop' unit='xdg-desktop-portal.service' requested by ':1.84' (uid=1000 pid=74048 comm="/usr/bin/gnome-software --gapplication-service" label="unconfined")
22:45:54 gnome-panel: Binding '<Super>S' failed!

22:45:53 kdeconnectd: Theme parsing error: gtk.css:15:25: '0' is not a valid color name
22:45:53 systemd: Started Tracker file system data miner.
22:45:53 nemo-desktop: Current gtk theme is not known to have nemo support (Radiance) - checking...
22:45:53 NetworkManager: <info>  [1669236353.5958] agent-manager: agent[7854c31a88f458b8,:1.514/org.freedesktop.nm-applet/1000]: agent registered
22:45:53 gsd-media-keys: Failed to grab accelerator for keybinding settings:rfkill
22:45:53 gtk-window-deco: Theme parsing error: gtk.css:15:25: '0' is not a valid color name
22:45:53 indicator-appli: Name Lost
22:45:53 nemo-desktop: Theme parsing error: gtk.css:15:25: '0' is not a valid color name
22:45:53 systemd: Started Application launched by gnome-session-binary.
22:45:53 gnome-session-b: GnomeDesktop-WARNING: Could not create transient scope for PID 74041: GDBus.Error:org.freedesktop.DBus.Error.UnixProcessIdUnknown: Process with ID 74041 does not exist.
22:45:53 nm-applet: Theme parsing error: gtk.css:15:25: '0' is not a valid color name
22:45:53 compiz: compiz (core) - Info: Starting plugin: scale
22:45:52 Xorg: (II) modeset(0): Modeline "1920x1080"x0.0  110.92  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (53.3 kHz e)
22:45:52 gsd-xsettings: Theme parsing error: gtk.css:15:25: '0' is not a valid color name
22:45:52 systemd: Starting Tracker file system data miner...
22:45:52 xkbcomp: Errors from xkbcomp are not fatal to the X server
22:45:52 compiz: Compiz (opengl) - Info: GLX_EXT_buffer_age is supported
22:45:52 gnome-panel: Theme parsing error: gtk.css:15:25: '0' is not a valid color name
22:45:52 gsd-usb-protect: Failed to fetch USBGuard parameters: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.usbguard1 was not provided by any .service files
22:45:52 compiz: compiz (core) - Info: Starting plugin: opengl
22:45:52 gsd-media-keys: Failed to grab accelerators: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: Object does not exist at path “/org/gnome/Shell”
22:45:52 systemd: Started Application launched by gnome-session-binary.
22:45:52 Xorg: (II) modeset(0): Modeline "1920x1080"x0.0  110.92  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (53.3 kHz e)
22:45:52 compiz: compiz (core) - Info: Starting plugin: composite
22:45:52 systemd: Reached target GNOME Wacom tablet support target.
22:45:52 kernel: rfkill: input handler disabled
22:45:52 systemd: Reached target GNOME maintenance of expirable data target.
22:45:52 compiz: compiz (core) - Info: Starting plugin: ccp
22:45:52 systemd: Reached target GNOME accessibility target.
22:45:52 spice-vdagent: vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0 does not exist, exiting
22:45:52 systemd: Failed to start IBus Daemon for GNOME.
22:45:52 ibus-daemon: current session already has an ibus-daemon.
22:45:52 systemd: Finished Signal initialization done to GNOME Session Manager.
22:45:52 compiz: compiz (core) - Info: Starting plugin: core
22:45:52 systemd: Starting GNOME XSettings service...
22:45:52 compiz: compiz (core) - Info: Loading plugin: core
22:45:52 systemd: Starting GNOME sound sample caching service...
22:45:52 gnome-flashback: Failed to grab accelerators: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: Object does not exist at path “/org/gnome/Shell”
22:45:52 systemd: Starting GNOME keyboard shortcuts service...
22:45:52 dbus-daemon: [session uid=1000 pid=73258] Successfully activated service 'org.gnome.Shell.Screencast'
22:45:52 polkitd: Registered Authentication Agent for unix-session:22 (system bus name :1.495 [/usr/bin/gnome-flashback], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
22:45:52 systemd: Started User preferences database.
22:45:52 dbus-daemon: [session uid=1000 pid=73258] Successfully activated service 'ca.desrt.dconf'

Regards!

---

