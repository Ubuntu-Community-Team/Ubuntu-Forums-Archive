---
title: "Cannot start gnome after upgrade to 11.10"
date: 2011-10-14
forum: Desktop Environments
---

### Post by ZedThou on 2011-10-14
Installed are gnome-panel, gnome-shell, gnome-session-fallback

At the graphical login screen there are options for "Gnome Classic" (with and without effects) and "Gnome Shell", but no matter what I choose, Unity is what starts up. Contents of .xsession-errors are pasted below, and I don't really know where else to look. Any ideas?

Thanks.

```

Running X session wrapper
Loading profile from /etc/profile
Loading profile from /home/rpete/.profile
Loading resource: /etc/X11/Xresources/x11-common
Loading X session script /etc/X11/Xsession.d/00_handle_guest_session
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
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Loading X session script /etc/X11/Xsession.d/90consolekit
Loading X session script /etc/X11/Xsession.d/90qt-a11y
Loading X session script /etc/X11/Xsession.d/90x11-common_ssh-agent
Loading X session script /etc/X11/Xsession.d/99x11-common_start
gnome-session[1784]: WARNING: Could not parse desktop file /home/rpete/.config/autostart/gkrellm.desktop: Key file does not have key 'Type'
gnome-session[1784]: WARNING: could not read /home/rpete/.config/autostart/gkrellm.desktop
GNOME_KEYRING_CONTROL=/tmp/keyring-DIJXEb
SSH_AUTH_SOCK=/tmp/keyring-DIJXEb/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-DIJXEb
SSH_AUTH_SOCK=/tmp/keyring-DIJXEb/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-DIJXEb
SSH_AUTH_SOCK=/tmp/keyring-DIJXEb/ssh
GPG_AGENT_INFO=/tmp/keyring-DIJXEb/gpg:0:1
GNOME_KEYRING_CONTROL=/tmp/keyring-DIJXEb
SSH_AUTH_SOCK=/tmp/keyring-DIJXEb/ssh
GPG_AGENT_INFO=/tmp/keyring-DIJXEb/gpg:0:1

(gnome-settings-daemon:1855): color-plugin-WARNING **: failed to get edid: unable to get EDID for output
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...yes
[LOG]: Moving Internal Files
[LOG]: Copying subdirectory from /home/rpete/.compiz/session to /home/rpete/.compiz-1/session
[LOG]: Copied file /home/rpete/.compiz/session/10718731ae998158d1131861168932106400000125330047 to /home/rpete/.compiz-1/session/10718731ae998158d1131861168932106400000125330047
[LOG]: Successfully moved internal files
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
common-plugin-Message: checking whether we have a device for 4: yes
common-plugin-Message: checking whether we have a device for 5: yes
common-plugin-Message: checking whether we have a device for 6: yes
common-plugin-Message: checking whether we have a device for 7: yes
common-plugin-Message: checking whether we have a device for 8: yes
common-plugin-Message: checking whether we have a device for 9: yes
common-plugin-Message: checking whether we have a device for 10: yes
** (gnome-fallback-mount-helper:1887): DEBUG: Starting automounting manager
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
** Message: applet now removed from the notification area
** (nm-applet:1882): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:1882): DEBUG: old state indicates that this was not a disconnect 0
** Message: using fallback from indicator to GtkStatusIcon
Initializing opengl options...done
Initializing decor options...done
Initializing move options...done
Initializing grid options...done
Initializing resize options...done
Initializing gnomecompat options...done
** (nautilus:1885): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged
** (gnome-fallback-mount-helper:1887): DEBUG: Found ConsoleKit session at path /org/freedesktop/ConsoleKit/Session2
** (gnome-fallback-mount-helper:1887): DEBUG: ScreenSaver name appeared
** (gnome-fallback-mount-helper:1887): DEBUG: ConsoleKit session is active 1
** (gnome-fallback-mount-helper:1887): DEBUG: ScreenSaver proxy ready
** (gnome-fallback-mount-helper:1887): DEBUG: Screensaver GetActive() returned 0
Initializing unitymtgrabhandles options...done
Initializing nautilus-gdu extension
Initializing snap options...done
Initializing vpswitch options...done
Initializing mousepoll options...done
Initializing place options...done
I/O warning : failed to load external entity "/home/rpete/.compiz/session/1029ed2ed610d265de131861195361513900000017840047"
Initializing session options...done
Initializing wall options...done
Initializing animation options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing fade options...done
Initializing workarounds options...done
Initializing ezoom options...done
Initializing scale options...done
** (process:1936): DEBUG: Telepathy Indicator started

(nautilus:1885): Gtk-CRITICAL **: gtk_action_set_visible: assertion `GTK_IS_ACTION (action)' failed

(nautilus:1885): Gtk-CRITICAL **: gtk_action_set_visible: assertion `GTK_IS_ACTION (action)' failed

Screen geometry changed:
   0x0x1920x1200

unity-panel-service: no process found
Initializing unityshell options...done
Starting unity-window-decorator
WARN  2011-10-14 13:06:03 unity.favorites FavoriteStoreGSettings.cpp:138 Unable to load GDesktopAppInfo for 'ubuntuone-control-panel-gtk.desktop'
WARN  2011-10-14 13:06:03 unity.favorites FavoriteStoreGSettings.cpp:121 Unable to load desktop file: /home/rpete/.gnome2/panel2.d/default/launchers/curly-00a0368abb-1.desktop
WARN  2011-10-14 13:06:03 unity.favorites FavoriteStoreGSettings.cpp:121 Unable to load desktop file: /home/rpete/.gnome2/panel2.d/default/launchers/frobate-006f87496e-1.desktop
DEBUG 2011-10-14 13:06:06 glib <unknown>:0 Setting to primary screen rect: x=0 y=0 w=1920 h=1200
compiz (core) - Warn: unhandled ConfigureNotify on 0x1600121!
compiz (core) - Warn: this should never happen. you shouldprobably file a bug about this.
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

** Message: moving back from GtkStatusIcon to indicator
WARN  2011-10-14 13:06:07 unity.launcher LauncherIcon.cpp:436 Unable to load '/usr/share/icons/hicolor/48x48/apps/firefox.png' icon: Failed to open file '/usr/share/icons/hicolor/48x48/apps/firefox.png': No such file or directory
Setting Update "main_menu_key"
Setting Update "run_key"
WARN  2011-10-14 13:06:11 unity.iconloader IconLoader.cpp:509 Unable to load contents of file:///usr/share/icons/hicolor/48x48/apps/firefox.png: Error opening file: No such file or directory
WARN  2011-10-14 13:06:11 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/music does not exist
WARN  2011-10-14 13:06:11 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/music does not exist
WARN  2011-10-14 13:06:11 unity.iconloader IconLoader.cpp:509 Unable to load contents of file:///usr/share/icons/hicolor/48x48/apps/firefox.png: Error opening file: No such file or directory
WARN  2011-10-14 13:06:11 unity.iconloader IconLoader.cpp:509 Unable to load contents of file:///usr/share/icons/hicolor/48x48/apps/firefox.png: Error opening file: No such file or directory
WARN  2011-10-14 13:06:11 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/files does not exist
WARN  2011-10-14 13:06:11 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/files does not exist
WARN  2011-10-14 13:06:13 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/commands does not exist
WARN  2011-10-14 13:06:13 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/commands does not exist
WARN  2011-10-14 13:06:13 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/applications does not exist
WARN  2011-10-14 13:06:13 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/applications does not exist
WARN  2011-10-14 13:06:13 unity.iconloader IconLoader.cpp:509 Unable to load contents of file:///usr/share/icons/unity-icon-theme/places/svg/category-installed.svg: Error opening file: No such file or directory
WARN  2011-10-14 13:06:13 unity.iconloader IconLoader.cpp:509 Unable to load contents of file:///usr/share/icons/unity-icon-theme/places/svg/category-available.svg: Error opening file: No such file or directory

** (process:2113): WARNING **: zeitgeist-datahub.vala:218: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
Could not check applicable rules for http://ubuntuforums.org/favicon.ico
Could not check applicable rules for http://ubuntuforums.org/forumdisplay.php?f=331
** (deja-dup-monitor:2586): DEBUG: monitor.vala:221: Automatic backups disabled.  Not scheduling a backup.

```

---

### Post by ZedThou on 2011-10-14
After stopping lightdm and starting gdm I can now use gnome classic and shell, although the choice of desktop isn't sticky. If I log out, then after entering my username the default desktop is still Ubuntu rather than my choice at last login. Both Gnome Shell and especially Unity are acting flaky.

---

