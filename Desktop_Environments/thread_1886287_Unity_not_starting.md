---
title: "Unity not starting"
date: 2011-11-24
forum: Desktop Environments
---

### Post by rangester on 2011-11-24
My Unity has ceased to work shortly after the update to 11.10. I think i have been messing around with my graphics drivers (ATI :( ), and that&#347; what caused it, but i&#7743; not sure anymore. Apparently this problem occurs a lot, but i have not been able to find a solution that worked for me. For reference, i think everything i have tried yet is in [here]("http://ubuntuforums.org/showthread.php?t=1872211&highlight=unity+-starting") and [here]("http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html"). Something curious i encountered at the instructions of the latter link, is that ```
sudo service gdm restart
``` returned ```
bas@ubuntu:~$ sudo service gdm restart
restart: Unknown instance: 
``` instead of doing anything useful.

I figured it might be useful to post what i get to see when i do unity --reset too, so here it is:

```
WARNING: Unity currently default profile, so switching to metacity while resetting the values
unity-panel-service: geen proces gevonden
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libopengl.so' : libGL.so.1: kan gedeeld objectbestand niet openen: Bestand of map bestaat niet
compiz (core) - Error: Couldn't load plugin 'opengl'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libdecor.so' : libGL.so.1: kan gedeeld objectbestand niet openen: Bestand of map bestaat niet
compiz (core) - Error: Couldn't load plugin 'decor'
Initializing mousepoll options...done
Initializing vpswitch options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libanimation.so' : libGL.so.1: kan gedeeld objectbestand niet openen: Bestand of map bestaat niet
compiz (core) - Error: Couldn't load plugin 'animation'
Initializing snap options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libexpo.so' : libGL.so.1: kan gedeeld objectbestand niet openen: Bestand of map bestaat niet
compiz (core) - Error: Couldn't load plugin 'expo'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libmove.so' : libGL.so.1: kan gedeeld objectbestand niet openen: Bestand of map bestaat niet
compiz (core) - Error: Couldn't load plugin 'move'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libcompiztoolbox.so' : libGL.so.1: kan gedeeld objectbestand niet openen: Bestand of map bestaat niet
compiz (core) - Error: Couldn't load plugin 'compiztoolbox'
Initializing place options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libgrid.so' : libGL.so.1: kan gedeeld objectbestand niet openen: Bestand of map bestaat niet
compiz (core) - Error: Couldn't load plugin 'grid'
Initializing gnomecompat options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libwall.so' : libGL.so.1: kan gedeeld objectbestand niet openen: Bestand of map bestaat niet
compiz (core) - Error: Couldn't load plugin 'wall'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libezoom.so' : libGL.so.1: kan gedeeld objectbestand niet openen: Bestand of map bestaat niet
compiz (core) - Error: Couldn't load plugin 'ezoom'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libworkarounds.so' : libGL.so.1: kan gedeeld objectbestand niet openen: Bestand of map bestaat niet
compiz (core) - Error: Couldn't load plugin 'workarounds'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libresize.so' : libGL.so.1: kan gedeeld objectbestand niet openen: Bestand of map bestaat niet
compiz (core) - Error: Couldn't load plugin 'resize'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libfade.so' : libGL.so.1: kan gedeeld objectbestand niet openen: Bestand of map bestaat niet
compiz (core) - Error: Couldn't load plugin 'fade'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libunitymtgrabhandles.so' : libGL.so.1: kan gedeeld objectbestand niet openen: Bestand of map bestaat niet
compiz (core) - Error: Couldn't load plugin 'unitymtgrabhandles'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libscale.so' : libGL.so.1: kan gedeeld objectbestand niet openen: Bestand of map bestaat niet
compiz (core) - Error: Couldn't load plugin 'scale'
Initializing session options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libunityshell.so' : libGL.so.1: kan gedeeld objectbestand niet openen: Bestand of map bestaat niet
compiz (core) - Error: Couldn't load plugin 'unityshell'
Initializing animation options...done
Initializing annotate options...done
Initializing blur options...done
Initializing clone options...done
Initializing colorfilter options...done
Initializing commands options...done
Initializing resize options...done
Initializing move options...done
Initializing cube options...done
Initializing debugspew options...done
Initializing decor options...done
Initializing expo options...done
Initializing ezoom options...done
Initializing fade options...done
Initializing grid options...done
Initializing imgjpeg options...done
Initializing kdecompat options...done
Initializing mag options...done
Initializing neg options...done
Initializing obs options...done
Initializing opacify options...done
Initializing opengl options...done
Initializing put options...done
Initializing resizeinfo options...done
Initializing ring options...done
Initializing rotate options...done
Initializing scale options...done
Initializing scaleaddon options...done
Initializing screenshot options...done
Initializing shift options...done
Initializing staticswitcher options...done
Initializing switcher options...done
Initializing thumbnail options...done
Initializing unitymtgrabhandles options...done
Initializing unityshell options...done
Initializing wall options...done
Initializing water options...done
Initializing winrules options...done
Initializing wobbly options...done
Initializing workarounds options...done
Initializing zoom options...done
Setting Update "main_menu_key"
Setting Update "run_key"
```

And then it does nothing anymore, no new line for putting commands in either, not sure if it&#347; supposed to work like that or not.

I hope there is a solution other than reinstalling ubuntu, i&#7743; starting to get bothered by the ugly fallback-gnome by now :X

---

### Post by LinuxFan999 on 2011-11-24
Try opening the terminal and typing this:
```
unity --reset
```

---

### Post by PayPaul on 2011-11-24
I have a similar problem or maybe had one. I installed compiz and tried some configuration changes. Apparently I lost unity in the process. Tried Unity -- reset but nothing seemed to work. I found that unity had been uninstalled so I attempted to reinstall it. Unity seems to be back but terminal is still running something. Here's what I've seen so far:

```
paulw@ubuntu:~$ unity
The program 'unity' is currently not installed.  You can install it by typing:
sudo apt-get install unity
paulw@ubuntu:~$ sudo apt-get install unity
[sudo] password for paulw: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kipi-plugins kipi-plugins-common gfortran-4.5 libblas-dev patchutils
  libncurses5-dev mysql-server-core-5.1 digikam-data libreadline6-dev
  libpcrecpp0 libqjson0 liblapack-dev akonadi-server mysql-client-core-5.1
  gfortran libpcre3-dev kdepim-runtime dpatch libbz2-dev libreadline-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  compiz compiz-core compiz-gnome compiz-plugins compiz-plugins-main
  compizconfig-backend-gconf libcompizconfig0
Suggested packages:
  compizconfig-settings-manager nvidia-glx gnome-themes
The following NEW packages will be installed:
  compiz compiz-core compiz-gnome compiz-plugins compiz-plugins-main
  compizconfig-backend-gconf libcompizconfig0 unity
0 upgraded, 8 newly installed, 0 to remove and 56 not upgraded.
Need to get 3,284 kB/3,912 kB of archives.
After this operation, 14.1 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ natty-updates/main compiz-core amd64 1:0.9.4+bzr20110606-0ubuntu1~natty2 [273 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ natty-updates/main compiz-plugins amd64 1:0.9.4+bzr20110606-0ubuntu1~natty2 [1,392 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ natty/main libcompizconfig0 amd64 0.9.4-0ubuntu2 [154 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ natty/main compizconfig-backend-gconf amd64 0.9.2.4-0ubuntu1 [19.6 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ natty-updates/main compiz-gnome amd64 1:0.9.4+bzr20110606-0ubuntu1~natty2 [132 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ natty-updates/main compiz-plugins-main amd64 0.9.4+bzr20110527-0ubuntu1~natty1 [1,309 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ natty-updates/main compiz all 1:0.9.4+bzr20110606-0ubuntu1~natty2 [5,492 B]
Fetched 3,284 kB in 6s (536 kB/s)                                              
Selecting previously deselected package compiz-core.
(Reading database ... 261352 files and directories currently installed.)
Unpacking compiz-core (from .../compiz-core_1%3a0.9.4+bzr20110606-0ubuntu1~natty2_amd64.deb) ...
Selecting previously deselected package compiz-plugins.
Unpacking compiz-plugins (from .../compiz-plugins_1%3a0.9.4+bzr20110606-0ubuntu1~natty2_amd64.deb) ...
Selecting previously deselected package libcompizconfig0.
Unpacking libcompizconfig0 (from .../libcompizconfig0_0.9.4-0ubuntu2_amd64.deb) ...
Selecting previously deselected package compizconfig-backend-gconf.
Unpacking compizconfig-backend-gconf (from .../compizconfig-backend-gconf_0.9.2.4-0ubuntu1_amd64.deb) ...
Selecting previously deselected package compiz-gnome.
Unpacking compiz-gnome (from .../compiz-gnome_1%3a0.9.4+bzr20110606-0ubuntu1~natty2_amd64.deb) ...
Selecting previously deselected package compiz-plugins-main.
Unpacking compiz-plugins-main (from .../compiz-plugins-main_0.9.4+bzr20110527-0ubuntu1~natty1_amd64.deb) ...
Selecting previously deselected package compiz.
Unpacking compiz (from .../compiz_1%3a0.9.4+bzr20110606-0ubuntu1~natty2_all.deb) ...
Selecting previously deselected package unity.
Unpacking unity (from .../unity_3.8.16-0ubuntu1~natty3_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for gconf2 ...
Processing triggers for python-support ...
Setting up compiz-core (1:0.9.4+bzr20110606-0ubuntu1~natty2) ...
Setting up compiz-plugins (1:0.9.4+bzr20110606-0ubuntu1~natty2) ...
Setting up libcompizconfig0 (0.9.4-0ubuntu2) ...
Setting up compizconfig-backend-gconf (0.9.2.4-0ubuntu1) ...
Setting up compiz-gnome (1:0.9.4+bzr20110606-0ubuntu1~natty2) ...
Setting up compiz-plugins-main (0.9.4+bzr20110527-0ubuntu1~natty1) ...
Setting up compiz (1:0.9.4+bzr20110606-0ubuntu1~natty2) ...
Setting up unity (3.8.16-0ubuntu1~natty3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
paulw@ubuntu:~$ install unity
install: missing destination file operand after `unity'
Try `install --help' for more information.
paulw@ubuntu:~$ unity
unity-panel-service: no process found
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing snap options...done
Initializing expo options...done
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing staticswitcher options...done
Initializing resize options...done
Initializing fade options...done
Initializing unitymtgrabhandles options...done
Initializing scale options...done
Initializing session options...done
** (<unknown>:3276): DEBUG: Unity accessibility initialization

Screen geometry changed:
  Monitor 0(primary)
   0x0x1024x768

unity-panel-service: no process found
** (<unknown>:3276): DEBUG: PanelController:: Added Panel for Monitor 0
Initializing unityshell options...done
** (<unknown>:3276): DEBUG: MaximizeIfBigEnough: Gnome-terminal window size doesn't fit
Starting unity-window-decorator
** (<unknown>:3276): DEBUG: PlaceEntry: Applications
** (<unknown>:3276): DEBUG: PlaceEntry: Commands
** (<unknown>:3276): DEBUG: PlaceEntry: Files & Folders
** (<unknown>:3276): DEBUG: /com/canonical/unity/applicationsplace
** (<unknown>:3276): DEBUG: /com/canonical/unity/filesplace
** (<unknown>:3276): DEBUG: Setting to primary screen rect: x=0 y=0 w=1024 h=768
** (<unknown>:3276): DEBUG: Acquired the name com.canonical.Unity.Launcher on the session bus

** (<unknown>:3276): DEBUG: TrayChild Rejected: gsd-xrandr gnome-settings-daemon Gnome-settings-daemon
** (<unknown>:3276): DEBUG: TrayChild Rejected: nm-applet nm-applet Nm-applet

(<unknown>:3276): Gdk-WARNING **: /build/buildd/gtk+2.0-2.24.4/gdk/x11/gdkdrawable-x11.c:942 drawable is not a native X11 window

(<unknown>:3276): Gdk-WARNING **: /build/buildd/gtk+2.0-2.24.4/gdk/x11/gdkdrawable-x11.c:942 drawable is not a native X11 window

(<unknown>:3276): Gdk-WARNING **: /build/buildd/gtk+2.0-2.24.4/gdk/x11/gdkdrawable-x11.c:942 drawable is not a native X11 window

(<unknown>:3276): Gdk-WARNING **: /build/buildd/gtk+2.0-2.24.4/gdk/x11/gdkdrawable-x11.c:942 drawable is not a native X11 window

(<unknown>:3276): Gdk-WARNING **: /build/buildd/gtk+2.0-2.24.4/gdk/x11/gdkdrawable-x11.c:942 drawable is not a native X11 window

(<unknown>:3276): Gdk-WARNING **: /build/buildd/gtk+2.0-2.24.4/gdk/x11/gdkdrawable-x11.c:942 drawable is not a native X11 window

(<unknown>:3276): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** (<unknown>:3276): DEBUG: IndicatorAdded: libapplication.so
** (<unknown>:3276): DEBUG: IndicatorAdded: libsoundmenu.so
** (<unknown>:3276): DEBUG: IndicatorAdded: libmessaging.so
** (<unknown>:3276): DEBUG: IndicatorAdded: libdatetime.so
** (<unknown>:3276): DEBUG: IndicatorAdded: libme.so
** (<unknown>:3276): DEBUG: IndicatorAdded: libsession.so
Setting Update "run_command_terminal_key"
Setting Update "fullscreen_visual_bell"
** (<unknown>:3276): DEBUG: Connected to proxy
** (<unknown>:3276): DEBUG: Connected to proxy
** (<unknown>:3276): DEBUG: Connected to proxy

(<unknown>:3276): GLib-GIO-CRITICAL **: g_bus_own_name: assertion `g_dbus_is_name (name) && !g_dbus_is_unique_name (name)' failed

(<unknown>:3276): GLib-GIO-CRITICAL **: g_bus_watch_name: assertion `g_dbus_is_name (name)' failed

(<unknown>:3276): GLib-GIO-CRITICAL **: g_bus_own_name: assertion `g_dbus_is_name (name) && !g_dbus_is_unique_name (name)' failed

(<unknown>:3276): GLib-GIO-CRITICAL **: g_bus_watch_name: assertion `g_dbus_is_name (name)' failed

(<unknown>:3276): GLib-GIO-CRITICAL **: g_dbus_connection_register_object: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed

(<unknown>:3276): GLib-GIO-CRITICAL **: g_dbus_connection_register_object: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed
** (<unknown>:3276): DEBUG: MaximizeIfBigEnough: window mapped and already maximized, just undecorate

(firefox:3393): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_menuitem_property_set_shortcut: assertion `gtk_accelerator_valid(key, modifier)' failed
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()

(npviewer.bin:3446): GLib-GObject-CRITICAL **: g_object_get_qdata: assertion `G_IS_OBJECT (object)' failed

(npviewer.bin:3446): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWindow'

(npviewer.bin:3446): Gtk-CRITICAL **: IA__gtk_window_get_type_hint: assertion `GTK_IS_WINDOW (window)' failed

(npviewer.bin:3446): GLib-GObject-CRITICAL **: g_object_get_qdata: assertion `G_IS_OBJECT (object)' failed

(npviewer.bin:3446): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWindow'

(npviewer.bin:3446): Gtk-CRITICAL **: IA__gtk_window_get_decorated: assertion `GTK_IS_WINDOW (window)' failed

(npviewer.bin:3446): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(npviewer.bin:3446): Gtk-CRITICAL **: IA__gtk_widget_get_toplevel: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:3446): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(npviewer.bin:3446): GLib-GObject-CRITICAL **: g_object_get_qdata: assertion `G_IS_OBJECT (object)' failed

(npviewer.bin:3446): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GtkWindow'

(npviewer.bin:3446): Gtk-CRITICAL **: IA__gtk_window_get_type_hint: assertion `GTK_IS_WINDOW (window)' failed

(npviewer.bin:3446): GLib-GObject-CRITICAL **: g_object_get_qdata: assertion `G_IS_OBJECT (object)' failed

(npviewer.bin:3446): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GtkWindow'

(npviewer.bin:3446): Gtk-CRITICAL **: IA__gtk_window_get_decorated: assertion `GTK_IS_WINDOW (window)' failed

(npviewer.bin:3446): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GtkWidget'

(npviewer.bin:3446): Gtk-CRITICAL **: IA__gtk_widget_get_toplevel: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:3446): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()

(npviewer.bin:3446): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(npviewer.bin:3446): Gtk-WARNING **: Loading IM context type 'ibus' failed


```

Can someone explain to me what some of this means? I don't like the last entry especially. 

What I'd been trying to do with compiz is modify the behavior of my windows so that they fit on my screen better.

---

### Post by stinkeye on 2011-11-25
**This is for 11.10**
Not too sure what you've uninstalled or changed, but this will restore compiz to defaults,
re-enable the unity plugin and then reload compiz.
Give it time to run.```
gconftool-2 --recursive-unset /apps/compiz-1 && gconftool-2 --type=list --list-type=string --set /apps/compiz-1/general/screen0/options/active_plugins [core,bailer,detection,composite,opengl,compiztoolbox,decor,grid,move,resize,mousepoll,regex,snap,gnomecompat,place,imgpng,vpswitch,animation,wall,workarounds,fade,session,expo,ezoom,unityshell] && compiz --replace & disown
```

---

### Post by stinkeye on 2011-11-25
> **rangester said:**
> My Unity has ceased to work shortly after the update to 11.10. I think i have been messing around with my graphics drivers (ATI :( ), and that&#347; what caused it, but i&#7743; not sure anymore. Apparently this problem occurs a lot, but i have not been able to find a solution that worked for me. For reference, i think everything i have tried yet is in [here]("http://ubuntuforums.org/showthread.php?t=1872211&highlight=unity+-starting") and [here]("http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html"). Something curious i encountered at the instructions of the latter link, is that ```
sudo service gdm restart
``` returned ```
bas@ubuntu:~$ sudo service gdm restart
restart: Unknown instance: 
``` instead of doing anything useful.



I hope there is a solution other than reinstalling ubuntu, i&#7743; starting to get bothered by the ugly fallback-gnome by now :X

In 11.10 you need to use 
```
sudo service **lightdm** restart
```

If you have  tried all the solutions and nothing works
you may have to bite the bullet and reinstall.
Usually after an upgrade removing all the compiz configs works.
eg 
```
rm -rf .gconf/apps/compiz*
rm -rf .cache/compizconfig-1/
rm -rf .config/compiz-1/
rm -rf .compiz*


```
Logout/in (make sure your logging in to the "Ubuntu" session) and run ccsm to check the Unity plugin is enabled.
If it is and you still don't see the unity panel and launcher
make sure your running compiz and not metacity as the window manager
```
compiz --replace & disown
```

Also check what vid driver your using
```
lspci -k | grep -A3 VGA
```

---

