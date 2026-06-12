---
title: "GUI crashing and burning"
date: 2011-06-03
forum: Desktop Environments
---

### Post by Shay Guy on 2011-06-03
OK, I probably should've come here before doing all the things I did to make this worse, but better late than never.

It started when I woke up to find that the Unity dock was misbehaving -- none of the icons were appearing, though there was something at the top that looked like a couple of the "flattened" icons that are usually at the bottom. I can't remember what I did in the terminal or gnome-system-monitor to try and fix this, but I *think* it was [FONT="Courier New"]unity --reset[/FONT]. (Should've been --replace, I know that now. Unless I was barking up the wrong tree altogether) The result was that the dock disappeared altogether along with the tops of all windows, much as has happened in the past when metacity crashed. But now alt-f2 wasn't working, and while I had a terminal open (and in front of all the other windows), I couldn't type anything into it. (I could, however, right-click and start a *new* terminal, which didn't work either.)

So then I switched to tty1-6. Unfortunately, I don't know how to use those to start things in tty7, only kill processes. I did some Googling and tried [FONT="Courier New"]sudo service gdm restart[/FONT]. This, according to [FONT="Courier New"]ps[/FONT], ended most of the processes I had open, and now tty7 is stuck on a text screen that says "[FONT="Courier New"]Ubuntu 11.04[/FONT]" at the top and "[FONT="Courier New"]* Checking battery state... [ OK ][/FONT]" at the bottom and has a blinking cursor at the bottom right. Ctrl-Alt-F8 opens a GUI login screen that lists me as "Currently logged in."

I'm completely lost here. Is there anything I can do to fix tty7? Is there even anything I should *bother* doing now but rebooting?

---

### Post by Shay Guy on 2011-06-03
I decided to give tty8 a shot. Unfortunately, even inside it, the top-left corner of my screen still looks like this, no matter how many times I restart Unity:

[IMG]http://dl.dropbox.com/u/2133352/badunityzoom.png[/IMG]

I tried running [FONT="Courier New"]unity -v[/FONT] from the terminal. Here's the output:

```
compiz (core) - Debug: Could not stat() file /home/myname/.compiz-1/plugins/libcore.so : No such file or directory
compiz (core) - Debug: Could not stat() file /usr/lib/compiz/libcore.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/myname/.compiz-1/plugins/libccp.so : No such file or directory
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
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
Window created on XQueryTree, map state isViewable? 1
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
compiz (core) - Debug: Could not stat() file /home/myname/.compiz-1/plugins/libbailer.so : No such file or directory
Initializing bailer options...done
compiz (core) - Debug: Could not stat() file /home/myname/.compiz-1/plugins/libdetection.so : No such file or directory
Initializing detection options...done
compiz (core) - Debug: Could not stat() file /home/myname/.compiz-1/plugins/libcomposite.so : No such file or directory
Initializing composite options...done
compiz (core) - Debug: Could not stat() file /home/myname/.compiz-1/plugins/libopengl.so : No such file or directory
Initializing opengl options...done
compiz (core) - Debug: Could not stat() file /home/myname/.compiz-1/plugins/libdecor.so : No such file or directory
Initializing decor options...done
compiz (core) - Debug: Could not stat() file /home/myname/.compiz-1/plugins/libmousepoll.so : No such file or directory
Initializing mousepoll options...done
compiz (core) - Debug: Could not stat() file /home/myname/.compiz-1/plugins/libvpswitch.so : No such file or directory
Initializing vpswitch options...done
compiz (core) - Debug: Could not stat() file /home/myname/.compiz-1/plugins/libregex.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/myname/.compiz-1/plugins/libanimation.so : No such file or directory
Initializing animation options...done
compiz (core) - Debug: Could not stat() file /home/myname/.compiz-1/plugins/libsnap.so : No such file or directory
Initializing snap options...done
compiz (core) - Debug: Could not stat() file /home/myname/.compiz-1/plugins/libexpo.so : No such file or directory
Initializing expo options...done
compiz (core) - Debug: Could not stat() file /home/myname/.compiz-1/plugins/libmove.so : No such file or directory
Initializing move options...done
compiz (core) - Debug: Could not stat() file /home/myname/.compiz-1/plugins/libcompiztoolbox.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/myname/.compiz-1/plugins/libplace.so : No such file or directory
Initializing place options...done
compiz (core) - Debug: Could not stat() file /home/myname/.compiz-1/plugins/libgrid.so : No such file or directory
Initializing grid options...done
compiz (core) - Debug: Could not stat() file /home/myname/.compiz-1/plugins/libimgpng.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/myname/.compiz-1/plugins/libgnomecompat.so : No such file or directory
Initializing gnomecompat options...done
compiz (core) - Debug: Could not stat() file /home/myname/.compiz-1/plugins/libwall.so : No such file or directory
Initializing wall options...done
compiz (core) - Debug: Could not stat() file /home/myname/.compiz-1/plugins/libezoom.so : No such file or directory
Initializing ezoom options...done
compiz (core) - Debug: Could not stat() file /home/myname/.compiz-1/plugins/libworkarounds.so : No such file or directory
Initializing workarounds options...done
compiz (core) - Debug: Could not stat() file /home/myname/.compiz-1/plugins/libstaticswitcher.so : No such file or directory
Initializing staticswitcher options...done
compiz (core) - Debug: Could not stat() file /home/myname/.compiz-1/plugins/libresize.so : No such file or directory
Initializing resize options...done
compiz (core) - Debug: Could not stat() file /home/myname/.compiz-1/plugins/libfade.so : No such file or directory
Initializing fade options...done
compiz (core) - Debug: Could not stat() file /home/myname/.compiz-1/plugins/libunitymtgrabhandles.so : No such file or directory
Initializing unitymtgrabhandles options...done
compiz (core) - Debug: Could not stat() file /home/myname/.compiz-1/plugins/libscale.so : No such file or directory
Initializing scale options...done
compiz (core) - Debug: Could not stat() file /home/myname/.compiz-1/plugins/libsession.so : No such file or directory
Initializing session options...done
compiz (core) - Debug: Could not stat() file /home/myname/.compiz-1/plugins/libunityshell.so : No such file or directory
** (<unknown>:32431): DEBUG: Unity accessibility initialization
** (<unknown>:32431): DEBUG: Shows on edge: 1

Screen geometry changed:
  Monitor 0(primary)
   0x0x1280x800

** (<unknown>:32431): DEBUG: PanelController:: Added Panel for Monitor 0
Initializing unityshell options...done
** (<unknown>:32431): DEBUG: MaximizeIfBigEnough: Gnome-terminal window size doesn't fit
** (<unknown>:32431): DEBUG: PlaceEntry: Applications
** (<unknown>:32431): DEBUG: PlaceEntry: Commands
** (<unknown>:32431): DEBUG: PlaceEntry: Files & Folders
** (<unknown>:32431): DEBUG: /com/canonical/unity/applicationsplace
** (<unknown>:32431): DEBUG: /com/canonical/unity/filesplace
** (<unknown>:32431): DEBUG: Setting to primary screen rect: x=0 y=0 w=1280 h=800
** (<unknown>:32431): DEBUG: Acquired the name com.canonical.Unity.Launcher on the session bus

** (<unknown>:32431): DEBUG: TrayChild Rejected: wicd-client.py wicd-client.py Wicd-client.py
** (<unknown>:32431): DEBUG: TrayChild Rejected: Pidgin Pidgin Pidgin
** (<unknown>:32431): DEBUG: Connected to proxy
** (<unknown>:32431): DEBUG: Connected to proxy
** (<unknown>:32431): DEBUG: Connected to proxy

(<unknown>:32431): GLib-GIO-CRITICAL **: g_bus_own_name: assertion `g_dbus_is_name (name) && !g_dbus_is_unique_name (name)' failed

(<unknown>:32431): GLib-GIO-CRITICAL **: g_bus_watch_name: assertion `g_dbus_is_name (name)' failed

(<unknown>:32431): GLib-GIO-CRITICAL **: g_bus_own_name: assertion `g_dbus_is_name (name) && !g_dbus_is_unique_name (name)' failed

(<unknown>:32431): GLib-GIO-CRITICAL **: g_bus_watch_name: assertion `g_dbus_is_name (name)' failed

(<unknown>:32431): GLib-GIO-CRITICAL **: g_dbus_connection_register_object: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed

(<unknown>:32431): GLib-GIO-CRITICAL **: g_dbus_connection_register_object: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed

(<unknown>:32431): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** (<unknown>:32431): DEBUG: IndicatorAdded: libapplication.so
** (<unknown>:32431): DEBUG: IndicatorAdded: libsoundmenu.so
** (<unknown>:32431): DEBUG: IndicatorAdded: libmessaging.so
** (<unknown>:32431): DEBUG: IndicatorAdded: libdatetime.so
** (<unknown>:32431): DEBUG: IndicatorAdded: libme.so
** (<unknown>:32431): DEBUG: IndicatorAdded: libsession.so
Setting Update "run_command_terminal_key"
Setting Update "fullscreen_visual_bell"

(<unknown>:32431): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(<unknown>:32431): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (<unknown>:32431): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window69206017: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:32431): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window69206017: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:32431): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window69206018: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:32431): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window69206018: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:32431): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window69206019: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:32431): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window69206019: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


(<unknown>:32431): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:32431): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:32431): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:32431): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed



```

And now I'm worried about the possibility of Unity still not working even after an actual restart. I've gotten used to it over the past month; going back to GNOME could be a pain in the hindquarters.

---

### Post by Shay Guy on 2011-06-05
Various tactics continue to fail. Restarting compiz (which is reading about 50% CPU usage; is that normal?) is among them. Also, I've somehow managed to get the terminal's "default" directory changed from /home/myname/ to /usr/bin/, any way to change that back? (Not the first time something like this has happened; I have to manually select "Memory" in Preferences every time I start [FONT="Courier New"]gnome-system-monitor[/FONT] to make it show up in the Processes tab. Been like that for ages; wasn't always.)

---

