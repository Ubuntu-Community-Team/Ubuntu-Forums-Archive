---
title: "GDM3 logins for non root users is broken 22.04.03"
date: 2023-10-10
forum: Desktop Environments
---

### Post by jimmyjump on 2023-10-10
Hello, 

I am not sure this is the right forum for this, if not please point me in the right direction.
I am running Ubuntu 22.04.03 with GDM3 Wayland.
Regarding unprivileged users, GDM works fine initially, however after installing a 3rd party package which installs some prerequisite packages  listed immediately below, unprivileged user GDM sessions break.

libqt5opengl5
libqt5quicktemplates2-5
libqt5quickcontrols2-5
libqt5quickparticles5
libnss-resolve
libonig5
libjq1
jq
systemd-coredump

After these packages are installed, I am experiencing issues with GDM3 logins for unprivileged users where the desktop background is a solid blue and where icons do not appear.
Additionally, attempts to launch any applications like Nautilus or gnome-terminal results in a systemd-coredump. 
If I login as root, GDM works perfectly, I find this encouraging because GDM actually works.. 

I have tried this below and it did not help to fix the icon issues or the core dumps.

update-mime-database /usr/share/mime
gdk-pixbuf-query-loaders --update-cache


Regarding unprivileged users, I see various errors in the journalctl output, the issue seems to be systemd or dbus related but I am guessing.

## Tracker is problematic 
testsystem systemd[3270]: Starting Tracker file system data miner...
testsystem dbus-daemon[3292]: [session uid=26114 pid=3292] Failed to activate service 'org.freedesktop.Tracker3.M
(service_start_timeout=120000ms)
testsystem tracker-extract[7969]: Could not connect to filesystem miner endpoint: GDBus.Error:org.freedesktop.DBu
activate service 'org.freedesktop.Tracker3.Miner.Files': timed out (service_start_timeout=120000ms)
testsystem tracker-miner-f[8038]: Could not delete '.meta.isrunning': No such file or directory
testsystem tracker-miner-f[8038]: Could not create store/endpoint: Database version is too old: got version 0, bu
needed

## DBUS entries
testsystem systemd[3270]: Starting Tracker file system data miner...
testsystem dbus-daemon[3292]: [session uid=26114 pid=3292] Failed to activate service 'org.freedesktop.Tracker3.M
(service_start_timeout=120000ms)
testsystem tracker-extract[7969]: Could not connect to filesystem miner endpoint: GDBus.Error:org.freedesktop.DBu
activate service 'org.freedesktop.Tracker3.Miner.Files': timed out (service_start_timeout=120000ms)
testsystem tracker-miner-f[8038]: Could not delete '.meta.isrunning': No such file or directory
testsystem tracker-miner-f[8038]: Could not create store/endpoint: Database version is too old: got version 0, bu
needed

## Desktop Integration entries -- the directory exists
testsystem systemd[4678]: Started Service for snap application snapd-desktop-integration.snapd-desktop-integration.
testsystem snapd-desktop-integration.snapd-desktop-integration[4688]: cmd_run.go:1046: WARNING: cannot create user data directory: cannot create snap home dir: mkdir /home/testuser: permission denied
testsystem systemd[4678]: snap.snapd-desktop-integration.snapd-desktop-integration.service: Main process exited, code=exited, status=1/FAILURE
testsystem snapd-desktop-integration.snapd-desktop-integration[4688]: cannot create user data directory: /home/testuser/snap/snapd-desktop-integration/83: Permission denied
testsystem systemd[4678]: snap.snapd-desktop-integration.snapd-desktop-integration.service: Failed with result 'exit-code'.
testsystem systemd[5015]: Started Service for snap application snapd-desktop-integration.snapd-desktop-integration.
testsystem systemd[5015]: snap.snapd-desktop-integration.snapd-desktop-integration.service: Scheduled restart job, restart counter is at 1.
testsystem systemd[5015]: Stopped Service for snap application snapd-desktop-integration.snapd-desktop-integration.
testsystem systemd[5015]: Started Service for snap application snapd-desktop-integration.snapd-desktop-integration.
testsystem dbus-daemon[5047]: [session uid=26114 pid=5047] Activating via systemd: service name='org.freedesktop.portal.Desktop' unit='xdg-desktop-portal.service' requested by ':1.39' (uid=26114 pid=5573 comm="/snap/snapd-desktop-integration/83/usr/bin/snapd-d" label="snap.snapd-desktop-integration.snapd-desktop-integration (enforce)")
testsystem systemd[3270]: Started Service for snap application snapd-desktop-integration.snapd-desktop-integration.
testsystem systemd[3270]: snap.snapd-desktop-integration.snapd-desktop-integration.service: Scheduled restart job, restart counter is at 1.
testsystem systemd[3270]: Stopped Service for snap application snapd-desktop-integration.snapd-desktop-integration.
testsystem systemd[3270]: Started Service for snap application snapd-desktop-integration.snapd-desktop-integration.
testsystem dbus-daemon[3292]: [session uid=26114 pid=3292] Activating via systemd: service name='org.freedesktop.portal.Desktop' unit='xdg-desktop-portal.service' requested by ':1.45' (uid=26114 pid=3614 comm="/snap/snapd-desktop-integration/83/usr/bin/snapd-d" label="snap.snapd-desktop-integration.snapd-desktop-integration (enforce)")
testsystem systemd[4678]: Started Service for snap application snapd-desktop-integration.snapd-desktop-integration.
testsystem snapd-desktop-integration.snapd-desktop-integration[4688]: cmd_run.go:1046: WARNING: cannot create user data directory: cannot create snap home dir: mkdir /home/testuser: permission denied
testsystem systemd[4678]: snap.snapd-desktop-integration.snapd-desktop-integration.service: Main process exited, code=exited, status=1/FAILURE
testsystem snapd-desktop-integration.snapd-desktop-integration[4688]: cannot create user data directory: /home/testuser/snap/snapd-desktop-integration/83: Permission denied


## Gnome shell
testsystem gnome-shell[3458]: Running GNOME Shell (using mutter 42.9) as a Wayland display server
testsystem gnome-shell[3458]: Added device '/dev/dri/card0' (vmwgfx) using non-atomic mode setting.
testsystem gnome-shell[3458]: VMware: No 3D enabled (0, Success).
testsystem gnome-shell[3458]: Using Wayland display name 'wayland-0'
testsystem gnome-shell[3458]: Unset XDG_SESSION_ID, getCurrentSessionProxy() called outside a user session. Asking logind directly.
testsystem gnome-shell[3458]: Will monitor session 4
testsystem gnome-shell[3458]: Failed to load image: Unrecognized image file format
testsystem gnome-shell[3458]: Telepathy is not available, chat integration will be disabled.
testsystem gnome-shell[3458]: Failed to load background 'file:///usr/share/backgrounds/sanmina_rev_logo_thumb.jpg': Unrecognized image file format
testsystem gnome-shell[3458]: Error looking up permission: GDBus.Error:org.freedesktop.portal.Error.NotFound: No entry for geolocation
testsystem gnome-shell[3458]: Could not load a pixbuf from icon theme.
testsystem gnome-shell[3458]: GNOME Shell started at Tue Oct 10 2023 17:28:43 GMT+0000 (UTC)
testsystem gnome-shell[3458]: Registering session with GDM
testsystem gnome-shell[3458]: DING: Detected async api for thumbnails
testsystem gnome-shell[3458]: DING: (gjs:3904): Gtk-WARNING **: 17:28:58.419: Could not load a pixbuf from icon theme.
testsystem gnome-shell[3458]: DING: This may indicate that pixbuf loaders or the mime database could not be found.
testsystem gnome-shell[3458]: DING: Exception while updating an icon: Failed to load /usr/share/icons/Yaru/256x256/mimetypes/text-x-generic.png: Unrecognized image file format
testsystem gnome-shell[3458]: DING: [email]_createEmblemedIcon@/usr/share/gnome-shell/extensions/ding@rastersoft.com/desktopIconItem.js[/email]:699:30
testsystem gnome-shell[3458]: DING: [email]_updateIcon@/usr/share/gnome-shell/extensions/ding@rastersoft.com/desktopIconItem.js[/email]:558:35
testsystem gnome-shell[3458]: DING: [email]FileItem@/usr/share/gnome-shell/extensions/ding@rastersoft.com/fileItem.js[/email]:62:14
testsystem gnome-shell[3458]: DING: _doReadAsync/</<@/usr/share/gnome-shell/extensions/ding@rastersoft.com/desktopManager.js:1158:47
testsystem gnome-shell[3458]: DING: @/usr/share/gnome-shell/extensions/ding@rastersoft.com/ding.js:159:9
testsystem gnome-shell[3458]: DING: GNOME nautilus 42.6
testsystem gnome-shell[3458]: ATK Bridge is disabled but a11y has already been enabled.
testsystem [email]ubuntu-appindicators@ubuntu.com[/email][3458]: unable to update icon for livepatch
testsystem [email]ubuntu-appindicators@ubuntu.com[/email][3458]: livepatch, Impossible to read image info from path '/usr/share/icons/Yaru/16x16/apps/livepatch.png': GdkPixbuf.PixbufError: Failed to recognize image format
testsystem [email]ubuntu-appindicators@ubuntu.com[/email][3458]: unable to update icon for livepatch
testsystem gnome-shell[3458]: Failed to load image: Unrecognized image file format
testsystem gnome-shell[3458]: JS ERROR: Failed to initialize fprintd service: Gio.IOErrorEnum: GDBus.Error:net.reactivated.Fprint.Error.NoSuchDevice: No devices available
testsystem [email]ubuntu-appindicators@ubuntu.com[/email][3458]: unable to update icon for livepatch
testsystem [email]ubuntu-appindicators@ubuntu.com[/email][3458]: livepatch, Impossible to read image info from path '/usr/share/icons/Yaru/16x16/apps/livepatch.png': GdkPixbuf.PixbufError: Failed to recognize image format
testsystem [email]ubuntu-appindicators@ubuntu.com[/email][3458]: unable to update icon for livepatch
testsystem gnome-shell[3458]: DING: Detected async api for thumbnails
testsystem gnome-shell[3458]: DING: (gjs:8269): Gtk-WARNING **: 18:06:29.797: Could not load a pixbuf from icon theme.
testsystem gnome-shell[3458]: DING: This may indicate that pixbuf loaders or the mime database could not be found.
testsystem gnome-shell[3458]: DING: Exception while updating an icon: Failed to load /usr/share/icons/Yaru/256x256/mimetypes/text-x-generic.png: Unrecognized image file format
testsystem gnome-shell[3458]: DING: [email]_createEmblemedIcon@/usr/share/gnome-shell/extensions/ding@rastersoft.com/desktopIconItem.js[/email]:699:30
testsystem gnome-shell[3458]: DING: [email]_updateIcon@/usr/share/gnome-shell/extensions/ding@rastersoft.com/desktopIconItem.js[/email]:558:35
testsystem gnome-shell[3458]: DING: [email]FileItem@/usr/share/gnome-shell/extensions/ding@rastersoft.com/fileItem.js[/email]:62:14
testsystem gnome-shell[3458]: DING: _doReadAsync/</<@/usr/share/gnome-shell/extensions/ding@rastersoft.com/desktopManager.js:1158:47
testsystem gnome-shell[3458]: DING: @/usr/share/gnome-shell/extensions/ding@rastersoft.com/ding.js:159:9
testsystem gnome-shell[3458]: DING: GNOME nautilus 42.6
testsystem gnome-shell[3458]: DING: # Error creating terminal: Message recipient disconnected from message bus without replying




## This is the output for gnome-terminal failure

testsystem systemd[3270]: Starting GNOME Terminal Server...
testsystem tracker-miner-f[8665]: Could not delete '.meta.isrunning': No such file or directory
testsystem tracker-miner-f[8665]: Could not create store/endpoint: Database version is too old: got version 0, bu
needed
testsystem dbus-daemon[3292]: [session uid=26114 pid=3292] Successfully activated service 'org.gnome.Terminal'
testsystem systemd[3270]: Started GNOME Terminal Server.
testsystem systemd[3270]: tracker-extract-3.service: Main process exited, code=exited, status=1/FAILURE
testsystem systemd[3270]: tracker-extract-3.service: Failed with result 'exit-code'.
testsystem systemd[3270]: Failed to start Tracker metadata extractor.
testsystem systemd[3270]: tracker-extract-3.service: Scheduled restart job, restart counter is at 42.
testsystem systemd[3270]: Stopped Tracker metadata extractor.
testsystem systemd[3270]: Starting Tracker metadata extractor...
testsystem gnome-terminal-[8677]: Could not load a pixbuf from icon theme.
                                                 This may indicate that pixbuf loaders or the mime database could not be found.
testsystem gnome-terminal-server[8677]: **
testsystem gnome-terminal-server[8677]: Gtk:ERROR:../../../../gtk/gtkiconhelper.c:494:ensure_surface_for_gicon: a
== NULL): Failed to load /usr/share/icons/Yaru/16x16/status/image-missing.png: Unrecognized image file forma

testsystem gnome-terminal-server[8677]: Bail out! Gtk:ERROR:../../../../gtk/gtkiconhelper.c:494:ensure_surface_fo
(error == NULL): Failed to load /usr/share/icons/Yaru/16x16/status/image-missing.png: Unrecognized image 
3)
testsystem audit[8677]: ANOM_ABEND auid=26114 uid=26114 gid=26118 ses=5 subj=unconfined pid=8677 comm="gnome-term
res=1
testsystem systemd[3270]: tracker-miner-fs-3.service: Main process exited, code=exited, status=1/FAILURE
testsystem systemd[3270]: tracker-miner-fs-3.service: Failed with result 'exit-code'.
testsystem systemd[3270]: Failed to start Tracker file system data miner.
testsystem systemd[3270]: tracker-miner-fs-3.service: Scheduled restart job, restart counter is at 677.
testsystem systemd[3270]: Stopped Tracker file system data miner.
testsystem systemd[3270]: Starting Tracker file system data miner...
testsystem systemd-coredump[8694]: Process 8677 (gnome-terminal-) of user 26114 [B]dumped core.
[/B]

### entries for gnome-shell
testsystem gnome-shell[3458]: Running GNOME Shell (using mutter 42.9) as a Wayland display server
testsystem gnome-shell[3458]: Added device '/dev/dri/card0' (vmwgfx) using non-atomic mode setting.
testsystem gnome-shell[3458]: VMware: No 3D enabled (0, Success).
testsystem gnome-shell[3458]: Using Wayland display name 'wayland-0'
testsystem gnome-shell[3458]: Unset XDG_SESSION_ID, getCurrentSessionProxy() called outside a user session. Asking logind directly.
testsystem gnome-shell[3458]: Will monitor session 4
testsystem gnome-shell[3458]: Failed to load image: Unrecognized image file format
testsystem gnome-shell[3458]: Telepathy is not available, chat integration will be disabled.
testsystem gnome-shell[3458]: Failed to load background 'file:///usr/share/backgrounds/sanmina_rev_logo_thumb.jpg': Unrecognized image file format
testsystem gnome-shell[3458]: Error looking up permission: GDBus.Error:org.freedesktop.portal.Error.NotFound: No entry for geolocation
testsystem gnome-shell[3458]: Could not load a pixbuf from icon theme.
testsystem gnome-shell[3458]: GNOME Shell started at Tue Oct 10 2023 17:28:43 GMT+0000 (UTC)
testsystem gnome-shell[3458]: Registering session with GDM
testsystem gnome-shell[3458]: DING: Detected async api for thumbnails
testsystem gnome-shell[3458]: DING: (gjs:3904): Gtk-WARNING **: 17:28:58.419: Could not load a pixbuf from icon theme.
testsystem gnome-shell[3458]: DING: This may indicate that pixbuf loaders or the mime database could not be found.
testsystem gnome-shell[3458]: DING: Exception while updating an icon: Failed to load /usr/share/icons/Yaru/256x256/mimetypes/text-x-generic.png: Unrecognized image file format
testsystem gnome-shell[3458]: DING: [email]_createEmblemedIcon@/usr/share/gnome-shell/extensions/ding@rastersoft.com/desktopIconItem.js[/email]:699:30
testsystem gnome-shell[3458]: DING: [email]_updateIcon@/usr/share/gnome-shell/extensions/ding@rastersoft.com/desktopIconItem.js[/email]:558:35
testsystem gnome-shell[3458]: DING: [email]FileItem@/usr/share/gnome-shell/extensions/ding@rastersoft.com/fileItem.js[/email]:62:14
testsystem gnome-shell[3458]: DING: _doReadAsync/</<@/usr/share/gnome-shell/extensions/ding@rastersoft.com/desktopManager.js:1158:47
testsystem gnome-shell[3458]: DING: @/usr/share/gnome-shell/extensions/ding@rastersoft.com/ding.js:159:9
testsystem gnome-shell[3458]: DING: GNOME nautilus 42.6
testsystem gnome-shell[3458]: ATK Bridge is disabled but a11y has already been enabled.
testsystem [email]ubuntu-appindicators@ubuntu.com[/email][3458]: unable to update icon for livepatch
testsystem [email]ubuntu-appindicators@ubuntu.com[/email][3458]: livepatch, Impossible to read image info from path '/usr/share/icons/Yaru/16x16/apps/livepatch.png': GdkPixbuf.PixbufError: Failed to recognize image format
testsystem [email]ubuntu-appindicators@ubuntu.com[/email][3458]: unable to update icon for livepatch
testsystem gnome-shell[3458]: Failed to load image: Unrecognized image file format
testsystem gnome-shell[3458]: JS ERROR: Failed to initialize fprintd service: Gio.IOErrorEnum: GDBus.Error:net.reactivated.Fprint.Error.NoSuchDevice: No devices available
testsystem [email]ubuntu-appindicators@ubuntu.com[/email][3458]: unable to update icon for livepatch
testsystem [email]ubuntu-appindicators@ubuntu.com[/email][3458]: livepatch, Impossible to read image info from path '/usr/share/icons/Yaru/16x16/apps/livepatch.png': GdkPixbuf.PixbufError: Failed to recognize image format
testsystem [email]ubuntu-appindicators@ubuntu.com[/email][3458]: unable to update icon for livepatch
testsystem gnome-shell[3458]: DING: Detected async api for thumbnails
testsystem gnome-shell[3458]: DING: (gjs:8269): Gtk-WARNING **: 18:06:29.797: Could not load a pixbuf from icon theme.
testsystem gnome-shell[3458]: DING: This may indicate that pixbuf loaders or the mime database could not be found.
testsystem gnome-shell[3458]: DING: Exception while updating an icon: Failed to load /usr/share/icons/Yaru/256x256/mimetypes/text-x-generic.png: Unrecognized image file format
testsystem gnome-shell[3458]: DING: [email]_createEmblemedIcon@/usr/share/gnome-shell/extensions/ding@rastersoft.com/desktopIconItem.js[/email]:699:30
testsystem gnome-shell[3458]: DING: [email]_updateIcon@/usr/share/gnome-shell/extensions/ding@rastersoft.com/desktopIconItem.js[/email]:558:35
testsystem gnome-shell[3458]: DING: [email]FileItem@/usr/share/gnome-shell/extensions/ding@rastersoft.com/fileItem.js[/email]:62:14
testsystem gnome-shell[3458]: DING: _doReadAsync/</<@/usr/share/gnome-shell/extensions/ding@rastersoft.com/desktopManager.js:1158:47
testsystem gnome-shell[3458]: DING: @/usr/share/gnome-shell/extensions/ding@rastersoft.com/ding.js:159:9
testsystem gnome-shell[3458]: DING: GNOME nautilus 42.6
testsystem gnome-shell[3458]: DING: # Error creating terminal: Message recipient disconnected from message bus without replying

If anyone can point me i the right direction I would greatly appreciate it. I can provide logs from coredumpctl or any other logs if necessary.

Thank you

---

