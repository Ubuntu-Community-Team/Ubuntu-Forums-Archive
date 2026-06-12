---
title: "Gnome 3 does not load anymore, after intalling Gnome shell themes"
date: 2011-12-04
forum: Desktop Environments
---

### Post by waqar on 2011-12-04
Ok so i installed 11.10 64 bit yesterday using WUBI. also intalled Gnome 3 as my default session, was loving it when i went to [http://www.webupd8.org/2011/10/4-beautiful-gnome-32-compatible-gtk.html](http://www.webupd8.org/2011/10/4-beautiful-gnome-32-compatible-gtk.html) to get some gone shell themes.

followed the instructions added the PPA  by Wbupd8 to get the themes and pasted the command for two themes in terminal. it worked allright except the shell theme did not change. Visited the official extensions website at Gnome.org. It said the Extension to allow me to change theme is not compatible with this version of gnome. ok, so restarted the Linux and Gnome would not load. the sound plays and I can right click the desktop. but gnome top bar after appearing twice for a second, disappears.

here is a copy of .Xsession-errors
Running X session wrapper
Loading profile from /etc/profile
Loading profile from /home/waqar/.profile
Loading resource: /etc/X11/Xresources/x11-common
Loading X session script /etc/X11/Xsession.d/20x11-common_process-args
Loading X session script /etc/X11/Xsession.d/30x11-common_xresources
Loading X session script /etc/X11/Xsession.d/40x11-common_xsessionrc
Loading X session script /etc/X11/Xsession.d/50_check_unity_support
Loading X session script /etc/X11/Xsession.d/50x11-common_determine-startup
Loading X session script /etc/X11/Xsession.d/52libcanberra-gtk3-module_add-to-gtk-modules
Loading X session script /etc/X11/Xsession.d/52libcanberra-gtk-module_add-to-gtk-modules
Loading X session script /etc/X11/Xsession.d/55gnome-session_gnomerc
Loading X session script /etc/X11/Xsession.d/60x11-common_localhost
Loading X session script /etc/X11/Xsession.d/60x11-common_xdg_path
Loading X session script /etc/X11/Xsession.d/60xdg-user-dirs-update
Loading X session script /etc/X11/Xsession.d/65compiz_profile-on-session
Loading X session script /etc/X11/Xsession.d/70gconfd_path-on-session
Loading X session script /etc/X11/Xsession.d/75dbus_dbus-launch
Loading X session script /etc/X11/Xsession.d/80appmenu
Loading X session script /etc/X11/Xsession.d/80appmenu-gtk3
Loading X session script /etc/X11/Xsession.d/80im-switch
Setting IM through im-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Loading X session script /etc/X11/Xsession.d/90consolekit
Loading X session script /etc/X11/Xsession.d/90qt-a11y
Loading X session script /etc/X11/Xsession.d/90x11-common_ssh-agent
Loading X session script /etc/X11/Xsession.d/99x11-common_start
GNOME_KEYRING_CONTROL=/tmp/keyring-kXYnIi
SSH_AUTH_SOCK=/tmp/keyring-kXYnIi/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-kXYnIi
SSH_AUTH_SOCK=/tmp/keyring-kXYnIi/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-kXYnIi
SSH_AUTH_SOCK=/tmp/keyring-kXYnIi/ssh
GPG_AGENT_INFO=/tmp/keyring-kXYnIi/gpg:0:1
GNOME_KEYRING_CONTROL=/tmp/keyring-kXYnIi
SSH_AUTH_SOCK=/tmp/keyring-kXYnIi/ssh
GPG_AGENT_INFO=/tmp/keyring-kXYnIi/gpg:0:1

(gnome-settings-daemon:1535): color-plugin-WARNING **: failed to get edid: unable to get EDID for output
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...yes
[LOG]: Moving Internal Files
[LOG]: Copying subdirectory from /home/waqar/.compiz/session to /home/waqar/.compiz-1/session
[LOG]: Copied file /home/waqar/.compiz/session/10d2035862bf7642ff132294036364336400000014670036 to /home/waqar/.compiz-1/session/10d2035862bf7642ff132294036364336400000014670036
[LOG]: Successfully moved internal files
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
** (gnome-fallback-mount-helper:1570): DEBUG: Starting automounting manager
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
** Message: applet now removed from the notification area
** (gnome-fallback-mount-helper:1570): DEBUG: Found ConsoleKit session at path /org/freedesktop/ConsoleKit/Session2
** (gnome-fallback-mount-helper:1570): DEBUG: ScreenSaver name appeared
** (gnome-fallback-mount-helper:1570): DEBUG: ConsoleKit session is active 1
** (gnome-fallback-mount-helper:1570): DEBUG: ScreenSaver proxy ready
** (gnome-fallback-mount-helper:1570): DEBUG: Screensaver GetActive() returned 0
** (nautilus:1572): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged
** (nm-applet:1579): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:1579): DEBUG: old state indicates that this was not a disconnect 0
Initializing resize options...done
Initializing gnomecompat options...done
** Message: using fallback from indicator to GtkStatusIcon
Initializing vpswitch options...done
Initializing snap options...done
Initializing place options...done
Initializing grid options...done
Initializing move options...done
Initializing mousepoll options...done
Initializing wall options...done
Initializing unitymtgrabhandles options...done
I/O warning : failed to load external entity "/home/waqar/.compiz/session/10af57be27aed4cde9132296495295672600000014670036"
Initializing session options...done
Initializing nautilus-gdu extension
Initializing animation options...done
Initializing fade options...done
Initializing scale options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing workarounds options...done
Initializing ezoom options...done

Screen geometry changed:
   0x0x1366x768

unity-panel-service: no process found
** (process:1616): DEBUG: Telepathy Indicator started
Initializing unityshell options...done
Starting unity-window-decorator
DEBUG 2011-12-04 07:16:00 glib <unknown>:0 Setting to primary screen rect: x=0 y=0 w=1366 h=768
WARN  2011-12-04 07:16:00 unity.favorites FavoriteStoreGSettings.cpp:138 Unable to load GDesktopAppInfo for 'ubiquity-gtkui.desktop'
** Message: moving back from GtkStatusIcon to indicator
Setting Update "main_menu_key"
Setting Update "run_key"
** (nm-applet:1579): DEBUG: old state indicates that this was not a disconnect 0
WARN  2011-12-04 07:16:20 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/files does not exist
WARN  2011-12-04 07:16:20 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/files does not exist
WARN  2011-12-04 07:16:20 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/music does not exist
WARN  2011-12-04 07:16:20 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/music does not exist
WARN  2011-12-04 07:16:20 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/applications does not exist
WARN  2011-12-04 07:16:20 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/applications does not exist
WARN  2011-12-04 07:16:20 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/commands does not exist
WARN  2011-12-04 07:16:20 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/commands does not exist
WARN  2011-12-04 07:16:21 unity.iconloader IconLoader.cpp:509 Unable to load contents of file:///usr/share/icons/unity-icon-theme/places/svg/category-installed.svg: Error opening file: No such file or directory
WARN  2011-12-04 07:16:21 unity.iconloader IconLoader.cpp:509 Unable to load contents of file:///usr/share/icons/unity-icon-theme/places/svg/category-available.svg: Error opening file: No such file or directory
** (process:1691): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (nm-applet:1579): DEBUG: foo_client_state_changed_cb
** (nm-applet:1579): DEBUG: foo_client_state_changed_cb
** (nautilus:1572): DEBUG: Got notification of SyncDaemon startup in NameOwnerChanged
** (deja-dup-monitor:1995): DEBUG: monitor.vala:221: Automatic backups disabled.  Not scheduling a backup.

(npviewer.bin:1960): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(npviewer.bin:1960): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
WARN  2011-12-04 07:32:33 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2011-12-04 07:42:56 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(npviewer.bin:1960): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(npviewer.bin:1960): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(npviewer.bin:1960): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(npviewer.bin:1960): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(npviewer.bin:1960): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

WARN  2011-12-04 08:15:34 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(npviewer.bin:1960): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
RemoveFilesRecursively: unlink dir: Directory not empty
RemoveFilesRecursively: unlink dir: Directory not empty
RemoveFilesRecursively: unlink dir: Directory not empty
RemoveFilesRecursively: unlink dir: Directory not empty
RemoveFilesRecursively: unlink dir: Directory not empty
RemoveFilesRecursively: unlink dir: Directory not empty
RemoveFilesRecursively: unlink dir: Directory not empty
RemoveFilesRecursively: unlink dir: Directory not empty
RemoveFilesRecursively: unlink dir: Directory not empty
RemoveFilesRecursively: unlink dir: Directory not empty
RemoveFilesRecursively: unlink dir: Directory not empty
RemoveFilesRecursively: unlink dir: Directory not empty
RemoveFilesRecursively: unlink dir: Directory not empty
RemoveFilesRecursively: unlink dir: Directory not empty
RemoveFilesRecursively: unlink dir: Directory not empty
RemoveFilesRecursively: unlink dir: Directory not empty
RemoveFilesRecursively: unlink dir: Directory not empty
** (plugin-container:2175): DEBUG: NP_Initialize
** (plugin-container:2175): DEBUG: NP_Initialize succeeded
WARN  2011-12-04 08:21:57 glib.glib-gobject <unknown>:0 instance of invalid non-instantiatable type `(null)'

(firefox:1772): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_menuitem_property_set_shortcut: assertion `gtk_accelerator_valid(key, modifier)' failed
compiz (core) - Warn: no exact match for ConfigureNotify on 0x180010a!
compiz (core) - Warn: expected the following changes:
compiz (core) - Warn: sibling: 0x43ee95
compiz (core) - Warn: instead got:
compiz (core) - Warn: x: 0
compiz (core) - Warn: y: 0
compiz (core) - Warn: width: 1366
compiz (core) - Warn: height: 768
compiz (core) - Warn: above: 0
compiz (core) - Warn: this should never happen. you should probably file a bug about this.

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
** (process:1691): DEBUG: desktop-launch-listener.vala:118: ran with uri: file:///home/waqar/.xsession-errors
** (process:1691): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (process:1691): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (process:1691): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
WARN  2011-12-04 08:24:08 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2011-12-04 08:24:08 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
** (process:1691): DEBUG: desktop-launch-listener.vala:118: ran with uri: file:///home/waqar/.xsession-errors
** (process:1691): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (process:1691): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
WARN  2011-12-04 08:25:28 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2011-12-04 08:25:28 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2011-12-04 08:25:29 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2011-12-04 08:25:34 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (gnome-fallback-mount-helper:1570): DEBUG: Screensaver active changed to 1
** (gnome-fallback-mount-helper:1570): DEBUG: Screensaver active changed to 0

(npviewer.bin:1960): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(npviewer.bin:1960): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(npviewer.bin:1960): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

WARN  2011-12-04 08:54:57 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(npviewer.bin:1960): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

WARN  2011-12-04 08:59:22 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(npviewer.bin:1960): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(npviewer.bin:1960): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
WARN  2011-12-04 09:49:16 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2011-12-04 09:49:16 glib.glib-gobject <unknown>:0 instance of invalid non-instantiatable type `<invalid>'
NOTE: child process received `Goodbye', closing down
** (plugin-container:2175): DEBUG: NP_Shutdown
NOTE: child process received `Goodbye', closing down
** (process:1691): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
WARN  2011-12-04 10:08:21 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2011-12-04 10:08:21 glib.glib-gobject <unknown>:0 instance with invalid (NULL) class pointer
** (process:1691): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
WARN  2011-12-04 10:08:27 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

** (nautilus:1572): WARNING **: Failed calling get_metadata_and_quick_tree_synced: Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/platform/linux/dbus_interface.py", line 571, in get_metadata_and_quick_tree_synced
    path)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/syncdaemon/interaction_interfaces.py", line 213, in get_metadata_and_quick_tree_synced
    mdobj = self.fs_manager.get_by_path(real_path)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/syncdaemon/filesystem_manager.py", line 781, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/waqar/.local/share/ubuntuone/shares'


(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
ioQ3 1.35urt linux-i386 Dec 20 2007
----- FS_Startup -----
Going through search path...

----------------------
11059 files in pk3 files
execing default.cfg
execing q3config.cfg
execing autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
QKEY found.
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1:
Calling SDL_Init(SDL_INIT_VIDEO)...
SDL_Init(SDL_INIT_VIDEO) passed.
Initializing OpenGL display
...setting mode -1: 1366 768
Using 8/8/8 Color bits, 24 depth, 8 stencil display.
GL_RENDERER: Mesa DRI Mobile Intel® GM45 Express Chipset x86/MMX/SSE2
Initializing OpenGL extensions
...GL_S3_s3tc not found
...using GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_EXT_texture_filter_anisotropic

GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Mobile Intel® GM45 Express Chipset x86/MMX/SSE2
GL_VERSION: 2.1 Mesa 7.11
GL_MAX_TEXTURE_SIZE: 8192
GL_MAX_ACTIVE_TEXTURES_ARB: 8

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(8-bits)
MODE: -1, 1366 x 768 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_LINEAR
picmip: 0
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: enabled
compressed textures: disabled
Initializing Shaders
----- finished R_Init -----
------ Initializing Sound ------
Initializing SDL audio driver...
SDL audio driver is "pulse".
SDL_AudioSpec:
  Format:   AUDIO_S16LSB
  Freq:     22050
  Samples:  256
  Channels: 2
Starting SDL audio callback...
SDL audio initialized.
----- Sound Info -----
    1 stereo
 8192 samples
   16 samplebits
    1 submission_chunk
22050 speed
0x99c28e8 dma buffer
No background file.
----------------------
Sound initialization successful.
--------------------------------
Sound memory manager started
Loading vm file vm/ui.qvm...
VM file ui compiled to 737597 bytes of code
ui loaded in 33931488 bytes on the hunk
UI menu load time = 306 milli seconds
UI menu load time = 188 milli seconds
16 bots parsed
13 crosshairs parsed
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: ubuntu.ubuntu-domain
Alias: ubuntu
IP: 127.0.1.1
stdin is not a tty, tty console mode failed
Requesting servers from the master...
CL_ServersResponsePacket
195 servers parsed (total 195)
CL_ServersResponsePacket
195 servers parsed (total 390)
CL_ServersResponsePacket
195 servers parsed (total 585)
CL_ServersResponsePacket
195 servers parsed (total 780)
CL_ServersResponsePacket
195 servers parsed (total 975)
CL_ServersResponsePacket
195 servers parsed (total 1170)
CL_ServersResponsePacket
137 servers parsed (total 1307)
33 servers listed in browser with 1142 players.
1274 servers not listed due to filters, packet loss or pings higher than 800
64.94.238.89:27961 resolved to 64.94.238.89:27961
Server is for low pings only
RE_Shutdown( 0 )
Hunk_Clear: reset the hunk ok
----- R_Init -----

GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Mobile Intel® GM45 Express Chipset x86/MMX/SSE2
GL_VERSION: 2.1 Mesa 7.11
GL_MAX_TEXTURE_SIZE: 8192
GL_MAX_ACTIVE_TEXTURES_ARB: 8

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(8-bits)
MODE: -1, 1366 x 768 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_LINEAR
picmip: 0
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: enabled
compressed textures: disabled
Initializing Shaders
----- finished R_Init -----
Loading vm file vm/ui.qvm...
VM file ui compiled to 737597 bytes of code
ui loaded in 33931488 bytes on the hunk
UI menu load time = 266 milli seconds
UI menu load time = 167 milli seconds
16 bots parsed
13 crosshairs parsed
94.213.55.36:27960 resolved to 94.213.55.36:27960
----- FS_Startup -----
Going through search path...

handle 1: music/mainmenu.wav
----------------------
22118 files in pk3 files
Need paks: @q3ut4/ut_rumble.pk3@q3ut4/ut_rumble.pk3
Loading "libcurl-3.dll"...********************
ERROR: Can not autodownload missing file(s), because the cURL library could not be loaded. 

********************
RE_Shutdown( 0 )
Hunk_Clear: reset the hunk ok
----- R_Init -----

GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Mobile Intel® GM45 Express Chipset x86/MMX/SSE2
GL_VERSION: 2.1 Mesa 7.11
GL_MAX_TEXTURE_SIZE: 8192
GL_MAX_ACTIVE_TEXTURES_ARB: 8

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(8-bits)
MODE: -1, 1366 x 768 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_LINEAR
picmip: 0
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: enabled
compressed textures: disabled
Initializing Shaders
----- finished R_Init -----
Loading vm file vm/ui.qvm...
VM file ui compiled to 737597 bytes of code
ui loaded in 33931488 bytes on the hunk
UI menu load time = 229 milli seconds
UI menu load time = 150 milli seconds
16 bots parsed
13 crosshairs parsed
----- FS_Startup -----
Going through search path...

----------------------
33177 files in pk3 files
8.6.15.92:27960 resolved to 8.6.15.92:27960
----- FS_Startup -----
Going through search path...

handle 1: music/mainmenu.wav
----------------------
44236 files in pk3 files
RE_Shutdown( 0 )
Hunk_Clear: reset the hunk ok
----- R_Init -----

GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Mobile Intel® GM45 Express Chipset x86/MMX/SSE2
GL_VERSION: 2.1 Mesa 7.11
GL_MAX_TEXTURE_SIZE: 8192
GL_MAX_ACTIVE_TEXTURES_ARB: 8

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(8-bits)
MODE: -1, 1366 x 768 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_LINEAR
picmip: 0
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: enabled
compressed textures: disabled
Initializing Shaders
----- finished R_Init -----
Loading vm file vm/ui.qvm...
VM file ui compiled to 737597 bytes of code
ui loaded in 33931488 bytes on the hunk
UI menu load time = 232 milli seconds
UI menu load time = 148 milli seconds
16 bots parsed
13 crosshairs parsed
Loading vm file vm/cgame.qvm...
VM file cgame compiled to 1617707 bytes of code
cgame loaded in 34383680 bytes on the hunk
stitched 0 LoD cracks
...loaded 13946 faces, 52 meshes, 171 trisurfs, 0 flares
^3WARNING: R_FindImageFile could not find 'sprites/foe2.tga' in shader 'sprites/foe'
^3Shader sprites/foe has a stage with no image
UI menu load time = 21 milli seconds
13 crosshairs parsed
CL_InitCGame: 11.85 seconds
61 msec to draw all images
Com_TouchMemory: 0 msec
^1[BsTrD]f34r^7 has taken the ^4Blue^7 flag!
^1[BsTrD]f34r^7 dropped the ^4Blue^7 flag!
Rasec returned the BLUE flag!
^1Fak^7 has taken the ^4Blue^7 flag!
STATs coming Soon
Rasec got a lead enema from pascochasco's retro M4.
kicks141 joined the red team.
kicks141 entered the game
STATs coming Soon
LcR managed to slow down cia.c@m!'s SR-8 round just a little.
^1Fak^7 captured the ^4Blue flag!
jDkiller danced the UMP tango to cia.c@m!'s sweet sweet music.
retardednapkin danced the UMP tango to cia.c@m!'s sweet sweet music.
Server: g_inactivity changed to 50
Server: g_respawnDelay changed to 10
Rasec danced the UMP tango to cia.c@m!'s sweet sweet music.
^1pascochasco^7 has taken the ^4Blue^7 flag!
^1pascochasco^7 dropped the ^4Blue^7 flag!
pascochasco managed to slow down LcR's SR-8 round just a little.
LcR danced the UMP tango to SiR_cAmPaLoT's sweet sweet music.
^1[BsTrD]f34r^7 has taken the ^4Blue^7 flag!
You were hit in the Kevlar by PAPANGU for 29% damage.
You were hit in the Kevlar by PAPANGU for 29% damage.
SiR_cAmPaLoT played 'catch the shiny bullet' with jDkiller's LR-300 rounds.
You hit Anonymous.mX in the Torso for 44% damage.
You hit Anonymous.mX in the Legs for 17% damage.
Anonymous.mX got a lead enema from kicks141's retro M4.
You were hit in the Arms by jDkiller for 17% damage.
You were hit in the Kevlar by jDkiller for 29% damage.
kicks141 played 'catch the shiny bullet' with jDkiller's LR-300 rounds.
jDkiller had 100% Health.
cia.c@m! played 'catch the shiny bullet' with jDkiller's LR-300 rounds.
Anonymous.mX disconnected
Fak played 'catch the shiny bullet' with Rasec's LR-300 rounds.
^1[BsTrD]f34r^7 dropped the ^4Blue^7 flag!
[BsTrD]f34r was on the wrong end of PAPANGU's G36.
^1pascochasco^7 has taken the ^4Blue^7 flag!
^1pascochasco^7 captured the ^4Blue flag!
PAPANGU got a lead enema from SiR_cAmPaLoT's retro M4.
^1pascochasco^7 (Patio Courtyard): ^3sry
Rasec has become a nasty stain thanks to LcR's HE gren.
^1(DEAD) [BsTrD]f34r^3: ^3wtf
^1pascochasco^7 (Patio Courtyard): ^3blockkk
Misu connected
LcR managed to slow down cia.c@m!'s SR-8 round just a little.
console: ^4 Keep Teams Balanced or CookieBot Will, suggest ^7pascochasco^7

cia.c@m! played 'catch the shiny bullet' with Rasec's LR-300 rounds.
You were hit in the Kevlar by jDkiller for 29% damage.
^1pascochasco^7 (Main Square Alley): ^3Negative
Misu joined the blue team.
Misu entered the game
[BsTrD]f34r played 'catch the shiny bullet' with Rasec's LR-300 rounds.
server:  West of Z Best 1459
Misu got a lead enema from Fak's retro M4.
retardednapkin got a lead enema from pascochasco's retro M4.
Server: timelimit changed to 13
LcR got a lead enema from pascochasco's retro M4.
You were hit in the Kevlar by jDkiller for 29% damage.
You were hit in the Kevlar by jDkiller for 29% damage.
You hit jDkiller in the Legs for 17% damage.
You were hit in the Kevlar by jDkiller for 29% damage.
kicks141 played 'catch the shiny bullet' with jDkiller's LR-300 rounds.
jDkiller had 83% Health.
^1Fak^7 has taken the ^4Blue^7 flag!
^1Fak^7 dropped the ^4Blue^7 flag!
Fak was on the wrong end of PAPANGU's G36.
PAPANGU returned the BLUE flag!
Misu connected
^1(DEAD) Fak^3: ^3meh
lifeadd joined the blue team.
lifeadd entered the game
SiR_cAmPaLoT played 'catch the shiny bullet' with Rasec's LR-300 rounds.
Rasec got a lead enema from pascochasco's retro M4.
pascochasco played 'catch the shiny bullet' with lifeadd's LR-300 rounds.
lifeadd managed to slow down cia.c@m!'s SR-8 round just a little.  NEEP NEEP!
[BsTrD]f34r was on the wrong end of retardednapkin's G36.
jDkiller managed to slow down cia.c@m!'s SR-8 round just a little.
Misu joined the blue team.
Misu entered the game
retardednapkin managed to slow down cia.c@m!'s SR-8 round just a little.
cia.c@m! played 'catch the shiny bullet' with Rasec's LR-300 rounds.
LcR got a lead enema from SiR_cAmPaLoT's retro M4.
SiR_cAmPaLoT played 'catch the shiny bullet' with lifeadd's LR-300 rounds.
lifeadd got a lead enema from pascochasco's retro M4.
jDkiller got a lead enema from pascochasco's retro M4.
^1Fak^7 has taken the ^4Blue^7 flag!
You were hit in the Arms by PAPANGU for 17% damage.
You were hit in the Kevlar by PAPANGU for 29% damage.
You were hit in the Kevlar by PAPANGU for 29% damage.
Rasec got a lead enema from Fak's retro M4.
You were hit in the Kevlar by PAPANGU for 29% damage.
kicks141 was on the wrong end of PAPANGU's G36.
PAPANGU had 13% Health.
^1Fak^7 captured the ^4Blue flag!
SiR_cAmPaLoT was on the wrong end of PAPANGU's G36.
jDkiller managed to slow down LcR's SR-8 round just a little.
pascochasco managed to slow down LcR's SR-8 round just a little.
Rasec managed to slow down cia.c@m!'s SR-8 round just a little.
LcR was torn asunder by [BsTrD]f34r's crass AK103.
^1[BsTrD]f34r^7 has taken the ^4Blue^7 flag!
PAPANGU managed to slow down cia.c@m!'s SR-8 round just a little.  NEEP NEEP!
cia.c@m! bled to death from PAPANGU's attacks.
Misu Dropped due to inactivity
You were hit in the Kevlar by retardednapkin for 29% damage.
You hit retardednapkin in the Torso for 44% damage.
You hit retardednapkin in the Torso for 44% damage.
You hit retardednapkin in the Torso for 44% damage.
retardednapkin got a lead enema from kicks141's retro M4.
Fak played 'catch the shiny bullet' with lifeadd's LR-300 rounds.
jDkiller bled to death from Fak's attacks.
^1(DEAD) Fak^3: ^3lolz
You were hit in the Kevlar by PAPANGU for 29% damage.
You were hit in the Head by PAPANGU for 100% damage.
kicks141 was on the wrong end of PAPANGU's G36.
PAPANGU had 100% Health.
^1[BsTrD]f34r^7 captured the ^4Blue flag!
SiR_cAmPaLoT was on the wrong end of PAPANGU's G36.
pascochasco played 'catch the shiny bullet' with Rasec's LR-300 rounds.
Fak has become a nasty stain thanks to LcR's HE gren.
LcR danced the UMP tango to cia.c@m!'s sweet sweet music.
lifeadd danced the UMP tango to cia.c@m!'s sweet sweet music.
lifeadd disconnected
Rasec managed to slow down cia.c@m!'s SR-8 round just a little.
You were hit in the Arms by jDkiller for 17% damage.
You hit jDkiller in the Legs for 17% damage.
You were hit in the Kevlar by PAPANGU for 29% damage.
You hit jDkiller in the Legs for 17% damage.
You hit jDkiller in the Arms for 17% damage.
You were hit in the Kevlar by PAPANGU for 29% damage.
You were hit in the Kevlar by jDkiller for 29% damage.
kicks141 played 'catch the shiny bullet' with jDkiller's LR-300 rounds.
jDkiller had 48% Health.
PAPANGU managed to slow down cia.c@m!'s SR-8 round just a little.
jDkiller got a lead enema from SiR_cAmPaLoT's retro M4.
retardednapkin got a lead enema from SiR_cAmPaLoT's retro M4.
Rasec was torn asunder by [BsTrD]f34r's crass AK103.
SiR_cAmPaLoT managed to slow down LcR's SR-8 round just a little.
^1[BsTrD]f34r^7 has taken the ^4Blue^7 flag!
pascochasco disconnected
^1[BsTrD]f34r^7 dropped the ^4Blue^7 flag!
[BsTrD]f34r was on the wrong end of PAPANGU's G36.
console: ^4 Keep Teams Balanced or CookieBot Will, suggest ^7pascochasco^7

You hit LcR in the Kevlar for 29% damage.
PAPANGU returned the BLUE flag!
PAPANGU got a lead enema from Fak's retro M4.
Fak bled to death from PAPANGU's attacks.
LcR danced the UMP tango to cia.c@m!'s sweet sweet music.
server:  West of Z Best 1459
p-ka-boo connected
Rasec managed to slow down cia.c@m!'s SR-8 round just a little.
^1cia.c@m!^7 has taken the ^4Blue^7 flag!
SiR_cAmPaLoT has become a nasty stain thanks to PAPANGU's HE gren.
You hit PAPANGU in the Helmet for 51% damage.
You hit PAPANGU in the Kevlar for 29% damage.
PAPANGU got a lead enema from kicks141's retro M4.
JPICKS19 connected
LaAle connected
^1cia.c@m!^7 captured the ^4Blue flag!
Fak played 'catch the shiny bullet' with jDkiller's LR-300 rounds.
JPICKS19 joined the blue team.
JPICKS19 entered the game
jDkiller got a lead enema from SiR_cAmPaLoT's retro M4.
Server: g_inactivity changed to 70
Server: g_respawnDelay changed to 8
[BsTrD]f34r bled to death from retardednapkin's attacks.
^1kicks141^7 has taken the ^4Blue^7 flag!
You were hit in the Arms by PAPANGU for 17% damage.
LcR got a lead enema from SiR_cAmPaLoT's retro M4.
You were hit in the Legs by PAPANGU for 17% damage.
You were hit in the Legs by JPICKS19 for 17% damage.
You hit PAPANGU in the Kevlar for 29% damage.
You hit PAPANGU in the Legs for 17% damage.
You were hit in the Kevlar by PAPANGU for 29% damage.
^1kicks141^7 dropped the ^4Blue^7 flag!
You were hit in the Arms by PAPANGU for 17% damage.
kicks141 was on the wrong end of PAPANGU's G36.
PAPANGU had 53% Health.
PAPANGU returned the BLUE flag!
PAPANGU played 'catch the shiny bullet' with JPICKS19's LR-300 rounds.
LaAle joined the red team.
LaAle entered the game
LcR managed to slow down cia.c@m!'s SR-8 round just a little.  NEEP NEEP!
Rasec was on the wrong end of LaAle's G36.
You hit Fak in the Helmet for 51% damage.
cia.c@m! was on the wrong end of PAPANGU's G36.
p-ka-boo joined the blue team.
Fak Server command overflow
p-ka-boo entered the game
retardednapkin bled to death from [BsTrD]f34r's attacks.
PapaNoElCabrone connected
LaAle played 'catch the shiny bullet' with jDkiller's LR-300 rounds.
JPICKS19 played 'catch the shiny bullet' with jDkiller's LR-300 rounds.
You were hit in the Kevlar by jDkiller for 29% damage.
You hit jDkiller in the Kevlar for 29% damage.
You hit jDkiller in the Arms for 17% damage.
You hit jDkiller in the Kevlar for 29% damage.
You hit jDkiller in the Kevlar for 29% damage.
jDkiller got a lead enema from kicks141's retro M4.
^1(DEAD) LaAle^3: ^3lol
^1SiR_cAmPaLoT^7 has taken the ^4Blue^7 flag!
[BsTrD]f34r managed to slow down p-ka-boo's SR-8 round just a little.  NEEP NEEP!
PAPANGU got a lead enema from SiR_cAmPaLoT's retro M4.
^1LaAle^3: ^3teams
You hit LcR in the Kevlar for 29% damage.
LcR got a lead enema from kicks141's retro M4.
^1SiR_cAmPaLoT^7 (Alley by Wood Pile): ^3^5 INCOMING RIGHT side
Server: g_inactivity changed to 50
Server: g_respawnDelay changed to 10
PapaNoElCabrone joined the red team.
PapaNoElCabrone entered the game
You were hit in the Kevlar by retardednapkin for 29% damage.
jDkiller managed to slow down cia.c@m!'s SR-8 round just a little.
You were hit in the Legs by retardednapkin for 17% damage.
You were hit in the Kevlar by retardednapkin for 29% damage.
kicks141 was on the wrong end of retardednapkin's G36.
retardednapkin had 100% Health.
console: ^1 Keep Teams Balanced or CookieBot Will, suggest ^7jDkiller^7

Rasec was BBQ'ed by SiR_cAmPaLoT's exploding monkey.
^1SiR_cAmPaLoT^7 captured the ^4Blue flag!
retardednapkin played 'catch the shiny bullet' with JPICKS19's LR-300 rounds.
JPICKS19 danced the UMP tango to cia.c@m!'s sweet sweet music.
cia.c@m! managed to slow down LcR's SR-8 round just a little.
LaAle managed to slow down p-ka-boo's SR-8 round just a little.
jDkiller got a whole lot of hole from PapaNoElCabrone's DE round.
LcR got a lead enema from SiR_cAmPaLoT's retro M4.
[BsTrD]f34r played 'catch the shiny bullet' with Rasec's LR-300 rounds.
You were hit in the Head by retardednapkin for 100% damage.
kicks141 was on the wrong end of retardednapkin's G36.
retardednapkin had 100% Health.
retardednapkin managed to slow down cia.c@m!'s SR-8 round just a little.  NEEP NEEP!
SiR_cAmPaLoT was on the wrong end of PAPANGU's G36.
LaAle got a whole lot of hole from p-ka-boo's DE round.
^1(DEAD) SiR_cAmPaLoT^3: ^3and thats why its 10-1 lol
^1(DEAD) LaAle^7 (Patio Courtyard): ^3inc right now
LcR danced the UMP tango to cia.c@m!'s sweet sweet music.
^4p-ka-boo^7 has taken the ^1Red^7 flag!
^4p-ka-boo^7 dropped the ^1Red^7 flag!
^4Rasec^7 has taken the ^1Red^7 flag!
server:  West of Z Rest 1336
jDkiller danced the UMP tango to cia.c@m!'s sweet sweet music.
Server: timelimit changed to 9
Timelimit hit.
^1SiR_cAmPaLoT^3: ^3gg
^1[BsTrD]f34r^3: ^3gg
^4retardednapkin^3: ^3take m down you man form up on me and take them down together
----- FS_Startup -----
Going through search path...

----------------------
55295 files in pk3 files
RE_Shutdown( 0 )
Hunk_Clear: reset the hunk ok
----- R_Init -----

GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Mobile Intel® GM45 Express Chipset x86/MMX/SSE2
GL_VERSION: 2.1 Mesa 7.11
GL_MAX_TEXTURE_SIZE: 8192
GL_MAX_ACTIVE_TEXTURES_ARB: 8

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(8-bits)
MODE: -1, 1366 x 768 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_LINEAR
picmip: 0
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: enabled
compressed textures: disabled
Initializing Shaders
----- finished R_Init -----
Loading vm file vm/ui.qvm...
VM file ui compiled to 737597 bytes of code
ui loaded in 33931488 bytes on the hunk
UI menu load time = 247 milli seconds
UI menu load time = 158 milli seconds
16 bots parsed
13 crosshairs parsed
Loading vm file vm/cgame.qvm...
VM file cgame compiled to 1617707 bytes of code
cgame loaded in 34383680 bytes on the hunk
stitched 8 LoD cracks
...loaded 11627 faces, 203 meshes, 457 trisurfs, 0 flares
^3WARNING: R_FindImageFile could not find 'sprites/foe2.tga' in shader 'sprites/foe'
^3Shader sprites/foe has a stage with no image
UI menu load time = 17 milli seconds
13 crosshairs parsed
CL_InitCGame:  7.93 seconds
42 msec to draw all images
Com_TouchMemory: 0 msec
PapaNoElCabrone joined the red team.
LcR joined the blue team.
jDkiller joined the blue team.
p-ka-boo joined the blue team.
retardednapkin joined the blue team.
JPICKS19 joined the blue team.
cia.c@m! joined the red team.
SiR_cAmPaLoT joined the red team.
kicks141 joined the red team.
SiR_cAmPaLoT entered the game
[BsTrD]f34r entered the game
jDkiller entered the game
retardednapkin entered the game
JPICKS19 entered the game
cia.c@m! entered the game
PAPANGU entered the game
kicks141 entered the game
STATs coming Soon
LaAle entered the game
p-ka-boo entered the game
Rasec entered the game
PapaNoElCabrone entered the game
LcR entered the game
^1SiR_cAmPaLoT^7 has taken the ^4Blue^7 flag!
^1SiR_cAmPaLoT^7 dropped the ^4Blue^7 flag!
^1cia.c@m!^7 has taken the ^4Blue^7 flag!
>Z<*Turtleheart* connected
^4retardednapkin^3: ^3follow me
JPICKS19 played 'catch the shiny bullet' with PapaNoElCabrone's LR-300 rounds.
^1[BsTrD]f34r^7 has taken the ^4Blue^7 flag!
p-ka-boo got a lead enema from SiR_cAmPaLoT's retro M4.
jDkiller bled to death from cia.c@m!'s attacks.
SiR_cAmPaLoT was torn asunder by PAPANGU's crass AK103.
^1[BsTrD]f34r^7 dropped the ^4Blue^7 flag!
[BsTrD]f34r was torn asunder by PAPANGU's crass AK103.
PAPANGU managed to slow down cia.c@m!'s SR-8 round just a little.  NEEP NEEP!
^1(DEAD) SiR_cAmPaLoT^7 (main north road): ^3sorry
^1LaAle^7 has taken the ^4Blue^7 flag!
^1LaAle^7 captured the ^4Blue flag!
LaAle managed to slow down LcR's SR-8 round just a little.
PapaNoElCabrone managed to slow down p-ka-boo's SR-8 round just a little.
^1kicks141^7 has taken the ^4Blue^7 flag!
^1kicks141^7 dropped the ^4Blue^7 flag!
You were hit in the Kevlar by p-ka-boo for 100% damage.
kicks141 managed to slow down p-ka-boo's SR-8 round just a little.
p-ka-boo had 100% Health.
LcR got a lead enema from SiR_cAmPaLoT's retro M4.
console: ^6Try our West Coast Server ^7/connect 208.167.243.205:27960

p-ka-boo returned the BLUE flag!
^4p-ka-boo^7 has taken the ^1Red^7 flag!
JPICKS19 danced the UMP tango to [BsTrD]f34r's sweet sweet music.
console: ^74 players on Z^6 Best ^7of ^6Z^7 ]3^60^7T^6S^7 playing ut4_subway

^4p-ka-boo^7 dropped the ^1Red^7 flag!
p-ka-boo danced the UMP tango to cia.c@m!'s sweet sweet music.
^1[BsTrD]f34r^7 has taken the ^4Blue^7 flag!
retardednapkin got a lead enema from SiR_cAmPaLoT's retro M4.
LaAle returned the RED flag!
Rasec Dropped due to inactivity
jDkiller was on the wrong end of LaAle's G36.
^1[BsTrD]f34r^7 captured the ^4Blue flag!
jDkiller joined the red team.
jDkiller entered the game
^1LaAle^7 has taken the ^4Blue^7 flag!
Rasec connected
^1LaAle^7 dropped the ^4Blue^7 flag!
LaAle played 'catch the shiny bullet' with JPICKS19's LR-300 rounds.
You hit JPICKS19 in the Legs for 11% damage.
You hit JPICKS19 in the Legs for 11% damage.
^1[BsTrD]f34r^7 has taken the ^4Blue^7 flag!
JPICKS19 danced the UMP tango to [BsTrD]f34r's sweet sweet music.
retardednapkin played 'catch the shiny bullet' with PapaNoElCabrone's LR-300 rounds.
Rasec joined the blue team.
Rasec entered the game
jDkiller was torn asunder by PAPANGU's crass AK103.
^1[BsTrD]f34r^7 captured the ^4Blue flag!
LcR was on the wrong end of LaAle's G36.
^1PapaNoElCabrone^7 has taken the ^4Blue^7 flag!
JPICKS19 got a lead enema from SiR_cAmPaLoT's retro M4.
^4retardednapkin^3: ^3form up on me attack together
cia.c@m! managed to slow down p-ka-boo's SR-8 round just a little.
^1PapaNoElCabrone^7 captured the ^4Blue flag!
You hit p-ka-boo in the Kevlar for 20% damage.
[BsTrD]f34r managed to slow down p-ka-boo's SR-8 round just a little.
console: ^4 Keep Teams Balanced or CookieBot Will, suggest ^7jDkiller^7

^1LaAle^7 has taken the ^4Blue^7 flag!
LcR disconnected
Misu connected
Rasec was on the wrong end of LaAle's G36.
jDkiller was torn asunder by PAPANGU's crass AK103.
^1LaAle^7 captured the ^4Blue flag!
JPICKS19 danced the UMP tango to SiR_cAmPaLoT's sweet sweet music.
retardednapkin danced the UMP tango to SiR_cAmPaLoT's sweet sweet music.
jDkiller joined the blue team.
jDkiller entered the game
server:  West of Z PrOs 2196
Server: timelimit changed to 12
p-ka-boo stepped on his own grenade.
^4(DEAD) retardednapkin^3: ^3damn fool
PAPANGU danced the UMP tango to cia.c@m!'s sweet sweet music.
LaAle played 'catch the shiny bullet' with Rasec's LR-300 rounds.
You hit jDkiller in the Kevlar for 20% damage.
You hit Rasec in the Kevlar for 20% damage.
You hit Rasec in the Kevlar for 20% damage.
Rasec danced the UMP tango to SiR_cAmPaLoT's sweet sweet music.
You were hit in the Kevlar by jDkiller for 29% damage.
You hit jDkiller in the Head for 50% damage.
jDkiller danced the UMP tango to SiR_cAmPaLoT's sweet sweet music.
You hit retardednapkin in the Torso for 30% damage.
You hit retardednapkin in the Torso for 30% damage.
You hit retardednapkin in the Legs for 11% damage.
retardednapkin danced the UMP tango to SiR_cAmPaLoT's sweet sweet music.
Misu joined the blue team.
Misu entered the game
p-ka-boo danced the UMP tango to SiR_cAmPaLoT's sweet sweet music.
JPICKS19 danced the UMP tango to SiR_cAmPaLoT's sweet sweet music.
^4(DEAD) retardednapkin^3: ^3fck
PapaNoElCabrone played 'catch the shiny bullet' with Rasec's LR-300 rounds.
You were hit in the Legs by Misu for 17% damage.
You hit Rasec in the Kevlar for 20% damage.
You were hit in the Kevlar by Rasec for 29% damage.
Rasec managed to slow down cia.c@m!'s SR-8 round just a little.
^1LaAle^7 has taken the ^4Blue^7 flag!
Misu danced the UMP tango to SiR_cAmPaLoT's sweet sweet music.
jDkiller managed to slow down cia.c@m!'s SR-8 round just a little.
^4p-ka-boo^3: ^3can we have someone who does something other than just talk?
^1LaAle^7 captured the ^4Blue flag!
You hit Misu in the Legs for 11% damage.
Misu got shredded to pieces by kicks141's Negev
cia.c@m! played 'catch the shiny bullet' with Rasec's LR-300 rounds.
JPICKS19 played 'catch the shiny bullet' with PapaNoElCabrone's LR-300 rounds.
^1LaAle^7 has taken the ^4Blue^7 flag!
^1LaAle^7 dropped the ^4Blue^7 flag!
LaAle played 'catch the shiny bullet' with Rasec's LR-300 rounds.
[BsTrD]f34r got a whole lot of hole from p-ka-boo's DE round.
Misu disconnected
p-ka-boo bled to death from cia.c@m!'s attacks.
^1PapaNoElCabrone^7 has taken the ^4Blue^7 flag!
You were hit in the Kevlar by Rasec for 29% damage.
kicks141 played 'catch the shiny bullet' with Rasec's LR-300 rounds.
Rasec had 22% Health.
JPICKS19 managed to slow down cia.c@m!'s SR-8 round just a little.
^1PapaNoElCabrone^7 dropped the ^4Blue^7 flag!
PapaNoElCabrone played 'catch the shiny bullet' with Rasec's LR-300 rounds.
^1LaAle^7 has taken the ^4Blue^7 flag!
^1LaAle^7 dropped the ^4Blue^7 flag!
LaAle got a whole lot of hole from Rasec's DE round.
[BsTrD]f34r was on the wrong end of jDkiller's G36.
Rasec managed to slow down cia.c@m!'s SR-8 round just a little.
^1cia.c@m!^7 has taken the ^4Blue^7 flag!
^1cia.c@m!^7 dropped the ^4Blue^7 flag!
cia.c@m! was torn asunder by PAPANGU's crass AK103.
PAPANGU bled to death from cia.c@m!'s attacks.
SiR_cAmPaLoT killed himself.
You were hit in the Kevlar by p-ka-boo for 100% damage.
kicks141 managed to slow down p-ka-boo's SR-8 round just a little.
p-ka-boo had 100% Health.
JPICKS19 returned the BLUE flag!
^4jDkiller^7 has taken the ^1Red^7 flag!
^4jDkiller^7 dropped the ^1Red^7 flag!
jDkiller danced the UMP tango to cia.c@m!'s sweet sweet music.
cia.c@m! played 'catch the shiny bullet' with JPICKS19's LR-300 rounds.
PapaNoElCabrone played 'catch the shiny bullet' with Rasec's LR-300 rounds.
p-ka-boo was on the wrong end of LaAle's G36.
Rasec got a lead enema from SiR_cAmPaLoT's retro M4.
LaAle returned the RED flag!
JPICKS19 danced the UMP tango to [BsTrD]f34r's sweet sweet music.
PAPANGU danced the UMP tango to [BsTrD]f34r's sweet sweet music.
^1[BsTrD]f34r^7 has taken the ^4Blue^7 flag!
jDkiller got a lead enema from SiR_cAmPaLoT's retro M4.
You were hit in the Arms by p-ka-boo for 50% damage.
JPICKS19 managed to slow down cia.c@m!'s SR-8 round just a little.
^1[BsTrD]f34r^7 captured the ^4Blue flag!
^1LaAle^7 has taken the ^4Blue^7 flag!
Rasec was on the wrong end of LaAle's G36.
^1LaAle^7 dropped the ^4Blue^7 flag!
LaAle was torn asunder by PAPANGU's crass AK103.
PapaNoElCabrone was on the wrong end of retardednapkin's G36.
p-ka-boo returned the BLUE flag!
PAPANGU got a lead enema from SiR_cAmPaLoT's retro M4.
[BsTrD]f34r managed to slow down cia.c@m!'s SR-8 round just a little.
p-ka-boo danced the UMP tango to cia.c@m!'s sweet sweet music.
server:  West of Z GoDs 2296
^1cia.c@m!^7 has taken the ^4Blue^7 flag!
Server: timelimit changed to 9
Misu connected
^1cia.c@m!^7 dropped the ^4Blue^7 flag!
cia.c@m! played 'catch the shiny bullet' with Rasec's LR-300 rounds.
Rasec returned the BLUE flag!
JPICKS19 got a lead enema from SiR_cAmPaLoT's retro M4.
retardednapkin was on the wrong end of LaAle's G36.
PapaNoElCabrone played 'catch the shiny bullet' with Rasec's LR-300 rounds.
Rasec was taken out by [BsTrD]f34r's PSG1. Plink!
Misu joined the blue team.
Misu entered the game
SiR_cAmPaLoT was torn asunder by PAPANGU's crass AK103.
^1LaAle^7 has taken the ^4Blue^7 flag!
[BsTrD]f34r managed to slow down p-ka-boo's SR-8 round just a little.
^1LaAle^7 captured the ^4Blue flag!
^1(DEAD) SiR_cAmPaLoT^3: ^3lol finally realised :
You hit p-ka-boo in the Kevlar for 20% damage.
You hit p-ka-boo in the Kevlar for 20% damage.
^4jDkiller^7 has taken the ^1Red^7 flag!
You were hit in the Arms by p-ka-boo for 50% damage.
kicks141 managed to slow down p-ka-boo's SR-8 round just a little.
p-ka-boo had 60% Health.
^4jDkiller^7 dropped the ^1Red^7 flag!
jDkiller played 'catch the shiny bullet' with PapaNoElCabrone's LR-300 rounds.
JPICKS19 managed to slow down cia.c@m!'s SR-8 round just a little.
[BsTrD]f34r returned the RED flag!
p-ka-boo was on the wrong end of LaAle's G36.
Misu got a lead enema from SiR_cAmPaLoT's retro M4.
retardednapkin played 'catch the shiny bullet' with PapaNoElCabrone's LR-300 rounds.
PapaNoElCabrone was torn asunder by PAPANGU's crass AK103.
Rasec danced the UMP tango to cia.c@m!'s sweet sweet music.
^4PAPANGU^7 has taken the ^1Red^7 flag!
^4PAPANGU^7 dropped the ^1Red^7 flag!
PAPANGU was on the wrong end of LaAle's G36.
----- CL_Shutdown -----
Closing SDL audio device...
SDL audio device shut down.
RE_Shutdown( 1 )
-----------------------
WARN  2011-12-04 10:20:59 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2011-12-04 10:20:59 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2011-12-04 10:21:03 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (process:1691): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events

(npviewer.bin:3343): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(npviewer.bin:3343): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(npviewer.bin:3343): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
WARN  2011-12-04 10:32:07 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (process:1691): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
NOTE: child process received `Goodbye', closing down
WARN  2011-12-04 10:32:11 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (process:1691): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
WARN  2011-12-04 10:49:40 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2011-12-04 10:53:20 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(npviewer.bin:3481): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
WARN  2011-12-04 10:56:51 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2011-12-04 10:56:51 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2011-12-04 10:56:51 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(npviewer.bin:3481): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(npviewer.bin:3481): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(npviewer.bin:3481): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

WARN  2011-12-04 11:18:53 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2011-12-04 11:19:43 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(npviewer.bin:3481): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

WARN  2011-12-04 11:20:52 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2011-12-04 11:35:47 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(npviewer.bin:3481): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(npviewer.bin:3481): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
WARN  2011-12-04 11:47:34 glib.glib-gobject <unknown>:0 instance of invalid non-instantiatable type `(null)'
** (process:1691): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (process:1691): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
2011-12-04 12:08:44,076 - softwarecenter.ui.gtk3.em - INFO - EM's: 17 15 21
2011-12-04 12:08:52,993 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2011-12-04 12:08:53,244 - softwarecenter.ui.gtk3.utils - INFO - Softwarecenter style provider for radiance Gtk theme: /usr/share/software-center/ui/gtk3/css/softwarecenter.css
WARN  2011-12-04 12:08:58 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


2011-12-04 12:09:01,766 - softwarecenter.ui.gtk3.app - INFO - software-center-agent finished with status 0

(gnome-screenshot:3803): GdkPixbuf-CRITICAL **: gdk_pixbuf_composite: assertion `dest_y >= 0 && dest_y + dest_height <= dest->height' failed
** (gnome-screenshot:3803): DEBUG: The GetProfileForWindow request failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.ColorManager was not provided by any .service files
WARN  2011-12-04 12:10:17 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2011-12-04 12:10:18 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (process:1691): DEBUG: zeitgeist-datahub.vala:174: Inserting 3 events

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
** (process:1691): DEBUG: desktop-launch-listener.vala:118: ran with uri: file:///home/waqar/Pictures/Screenshot%20at%202011-12-04%2012:10:10.png
** (process:1691): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events

(gimp-2.6:3829): GLib-WARNING **: /build/buildd/glib2.0-2.30.0/./glib/goption.c:2168: ignoring no-arg, optional-arg or filename flags (8) on option of type 0
** (process:1691): DEBUG: zeitgeist-datahub.vala:174: Inserting 3 events
WARN  2011-12-04 12:10:38 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(gimp-2.6:3829): GLib-GObject-WARNING **: invalid cast from `GimpView' to `GtkImage'
** (process:1691): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x4a00003

WARN  2011-12-04 12:12:07 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
** (process:1691): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(gimp-2.6:3829): Gimp-Widgets-WARNING **: gimp_dialog_factory_dispose: stale non-toplevel entries in factory->open_dialogs

WARN  2011-12-04 12:13:32 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2011-12-04 12:13:32 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2011-12-04 12:13:32 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (process:1691): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (process:1691): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1572): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
** (process:1691): DEBUG: desktop-launch-listener.vala:118: ran with uri: file:///home/waqar/.xsession-errors
** (process:1691): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (process:1691): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events

---

### Post by vanlong441 on 2011-12-04
your gnome-shell broke. Now log into the fallback mode -> delete the theme you chose in /home/username/.themes and /usr/share/themes, log back to your gnome-shell mode. 

you can only use Firefox in extensions.gnome.org for now

the program you need to apply the theme is called gnome tweak tool. Every needed step to customize gnome-shell can be found here [http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html)

---

### Post by waqar on 2011-12-04
> **vanlong441 said:**
> your gnome-shell broke. Now log into the fallback mode -> delete the theme you chose in /home/username/.themes and /usr/share/themes, log back to your gnome-shell mode. 

you can only use Firefox in extensions.gnome.org for now

the program you need to apply the theme is called gnome tweak tool. Every needed step to customize gnome-shell can be found here [http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html)


Actually I removed them after searching them in Ubuntu Software Centre, and now they dont exist in the locations you mentioned. I am currently using unity anf Gome 3 still would not load, I reinstalled it  after removing many times but still no luck. Attached is the screen-shot of the software center history.

---

### Post by vanlong441 on 2011-12-04
sorry I cannot help any further. The problem I had with changing theme the last time did not go well either. I had to reinstall the OS.
My last suggestion: remove gnome-shell. Then manually delete these folders:
~/.local/share/gnome-shell
~/.themes
/usr/share/themes
/usr/share/gnome-shell

You may want to delete gnome-shell section in here, too
/usr/share/gnome-session/sessions

---

### Post by waqar on 2011-12-04
manually delete these folders:
~/.local/share/gnome-shell

well only delted the top folder and :popcorn::KS its back on ...


well let me say..

thaaaaaaaaaaaaaaank you.

---

### Post by vanlong441 on 2011-12-04
anytime waqar :D

---

### Post by waqar on 2011-12-04
Well it had something to do with the gnome alternate status menu. apparently if you have no pic in logg off menu, gnome crashes and fails to load,  deleting ~/.local/share/gnome-shell removes the extensions, put the picture and reinstall the extensions, working like a charm now.:)

---

### Post by vanlong441 on 2011-12-04
make sure you are using extensions from extensions.gnome.org.

---

### Post by nilarimogard on 2011-12-05
waqar is right, installing alternate status menu Shell extension from the official GNOME Shell extensions website will make GNOME Shell crash if you do not set a profile picture for your user. This doesn't happen if you use the same extension from the WebUpd8 GNOME 3 PPA...

---

