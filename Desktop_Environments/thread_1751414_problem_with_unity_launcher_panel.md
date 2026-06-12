---
title: "problem with unity launcher panel"
date: 2011-05-06
forum: Desktop Environments
---

### Post by amiragha on 2011-05-06
i've recently upgraded to 11.04 and i have big problem with apps that i added to the launcher panel including chromium, kate ...

the problem is when i minimize a page there is no white arrow(i don't know what it is called) like default app beside the app's launcher, so i have no access to the window I,ve just minimized. and when i click the launcher again it open a new window()

another problem is that i can't open multiple terminals from launcher(i can do it for firefox)

i don't want to but maybe it's better to go to the classical desktop

---

### Post by Paulgirardin on 2011-05-06
Try using the following command in terminal.
```
Unity --reset
```

Middle click on the launcher icon should open new instances of the terminal.

It can also be done via the key board
see here: [http://askubuntu.com/questions/28086/unity-keyboard-mouse-shortcuts](http://askubuntu.com/questions/28086/unity-keyboard-mouse-shortcuts)

---

### Post by amiragha on 2011-05-07
thanks 
it seems that there is a failure, the output of unity --reset is:


** (<unknown>:3560): DEBUG: Unity accessibility initialization

** (<unknown>:3560): WARNING **: Unable to load GDesktopAppInfo for 'kate.desktop'

(<unknown>:3560): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

Screen geometry changed:
  Monitor 0(primary)
   0x0x1280x800

unity-panel-service: no process found
** (<unknown>:3560): DEBUG: PanelController:: Added Panel for Monitor 0
Initializing unityshell options...done
** (<unknown>:3560): DEBUG: MaximizeIfBigEnough: Gnome-terminal window size doesn't fit
** (<unknown>:3560): DEBUG: PlaceEntry: Applications
** (<unknown>:3560): DEBUG: PlaceEntry: Commands
** (<unknown>:3560): DEBUG: PlaceEntry: Files & Folders
** (<unknown>:3560): DEBUG: /com/canonical/unity/applicationsplace
** (<unknown>:3560): DEBUG: /com/canonical/unity/filesplace
** (<unknown>:3560): DEBUG: Setting to primary screen rect: x=0 y=0 w=1280 h=800

** (<unknown>:3560): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window71303516: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

** (<unknown>:3560): DEBUG: Acquired the name com.canonical.Unity.Launcher on the session bus


** (<unknown>:3560): WARNING **: Failed to fetch view type at /org/ayatana/bamf/application0x8b3a9f0: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:3560): WARNING **: Failed to fetch view type at /org/ayatana/bamf/application0x8b3a9f0: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

** (<unknown>:3560): DEBUG: TrayChild Rejected: (null) goldendict Goldendict

** (<unknown>:3560): WARNING **: Unable to load GDesktopAppInfo for 'kate.desktop'

(<unknown>:3560): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

** (<unknown>:3560): WARNING **: Unable to load GDesktopAppInfo for 'kate.desktop'

(<unknown>:3560): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** (<unknown>:3560): DEBUG: Connected to proxy
** (<unknown>:3560): DEBUG: Connected to proxy
** (<unknown>:3560): DEBUG: Connected to proxy

(<unknown>:3560): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(<unknown>:3560): GLib-GIO-CRITICAL **: g_bus_own_name: assertion `g_dbus_is_name (name) && !g_dbus_is_unique_name (name)' failed

(<unknown>:3560): GLib-GIO-CRITICAL **: g_bus_watch_name: assertion `g_dbus_is_name (name)' failed

(<unknown>:3560): GLib-GIO-CRITICAL **: g_bus_own_name: assertion `g_dbus_is_name (name) && !g_dbus_is_unique_name (name)' failed

(<unknown>:3560): GLib-GIO-CRITICAL **: g_bus_watch_name: assertion `g_dbus_is_name (name)' failed

(<unknown>:3560): GLib-GIO-CRITICAL **: g_dbus_connection_register_object: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed

(<unknown>:3560): GLib-GIO-CRITICAL **: g_dbus_connection_register_object: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed
** (<unknown>:3560): DEBUG: IndicatorAdded: libapplication.so
** (<unknown>:3560): DEBUG: IndicatorAdded: libsoundmenu.so
** (<unknown>:3560): DEBUG: IndicatorAdded: libmessaging.so
** (<unknown>:3560): DEBUG: IndicatorAdded: libdatetime.so
** (<unknown>:3560): DEBUG: IndicatorAdded: libme.so
** (<unknown>:3560): DEBUG: IndicatorAdded: libsession.so
Setting Update "run_command_terminal_key"
Setting Update "fullscreen_visual_bell"

** (<unknown>:3560): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window67122330: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

what is wrong?

---

