---
title: "Unity freeze"
date: 2011-05-15
forum: Desktop Environments
---

### Post by 3ar1 on 2011-05-15
Hello,

I'm experiencing unity freezes every time I click a contact in evolution. Everything else works just fine, I can read and write mails, edit the calendar but can't even view contacts. Evolution seems to crash and causes unity to freeze. After getting a terminal with CTRL+ALT+t and issuing a

```
unity --reset
```

unity works again but I have to kill evolution. Does anyone have an idea what's wrong? Here's the output of the "untiy --reset":

```
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
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
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
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
** (<unknown>:3204): DEBUG: Unity accessibility initialization
** (<unknown>:3204): DEBUG: Shows on edge: 1

Screen geometry changed:
  Monitor 0(primary)
   0x0x1366x768

unity-panel-service: no process found
** (<unknown>:3204): DEBUG: PanelController:: Added Panel for Monitor 0
Initializing unityshell options...done
** (<unknown>:3204): DEBUG: MaximizeIfBigEnough: Gnome-terminal window size doesn't fit
** (<unknown>:3204): DEBUG: MaximizeIfBigEnough: Gnome-terminal window size doesn't fit
** (<unknown>:3204): DEBUG: PlaceEntry: Applications
** (<unknown>:3204): DEBUG: PlaceEntry: Commands
** (<unknown>:3204): DEBUG: PlaceEntry: Files & Folders
** (<unknown>:3204): DEBUG: /com/canonical/unity/applicationsplace
** (<unknown>:3204): DEBUG: /com/canonical/unity/filesplace
** (<unknown>:3204): DEBUG: Setting to primary screen rect: x=0 y=0 w=1366 h=768

** (<unknown>:3204): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window75538692: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:3204): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window75538743: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

** (<unknown>:3204): DEBUG: Acquired the name com.canonical.Unity.Launcher on the session bus


(<unknown>:3204): Gdk-WARNING **: /build/buildd/gtk+2.0-2.24.4/gdk/x11/gdkdrawable-x11.c:942 drawable is not a native X11 window

(<unknown>:3204): Gdk-WARNING **: /build/buildd/gtk+2.0-2.24.4/gdk/x11/gdkdrawable-x11.c:942 drawable is not a native X11 window

(<unknown>:3204): Gdk-WARNING **: /build/buildd/gtk+2.0-2.24.4/gdk/x11/gdkdrawable-x11.c:942 drawable is not a native X11 window

(<unknown>:3204): Gdk-WARNING **: /build/buildd/gtk+2.0-2.24.4/gdk/x11/gdkdrawable-x11.c:942 drawable is not a native X11 window

(<unknown>:3204): Gdk-WARNING **: /build/buildd/gtk+2.0-2.24.4/gdk/x11/gdkdrawable-x11.c:942 drawable is not a native X11 window

(<unknown>:3204): Gdk-WARNING **: /build/buildd/gtk+2.0-2.24.4/gdk/x11/gdkdrawable-x11.c:942 drawable is not a native X11 window
** (<unknown>:3204): DEBUG: Connected to proxy
** (<unknown>:3204): DEBUG: Connected to proxy
** (<unknown>:3204): DEBUG: Connected to proxy

(<unknown>:3204): GLib-GIO-CRITICAL **: g_bus_own_name: assertion `g_dbus_is_name (name) && !g_dbus_is_unique_name (name)' failed

(<unknown>:3204): GLib-GIO-CRITICAL **: g_bus_watch_name: assertion `g_dbus_is_name (name)' failed

(<unknown>:3204): GLib-GIO-CRITICAL **: g_bus_own_name: assertion `g_dbus_is_name (name) && !g_dbus_is_unique_name (name)' failed

(<unknown>:3204): GLib-GIO-CRITICAL **: g_bus_watch_name: assertion `g_dbus_is_name (name)' failed

(<unknown>:3204): GLib-GIO-CRITICAL **: g_dbus_connection_register_object: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed

(<unknown>:3204): GLib-GIO-CRITICAL **: g_dbus_connection_register_object: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed

(<unknown>:3204): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(<unknown>:3204): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:3204): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:3204): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:3204): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:3204): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:3204): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:3204): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:3204): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:3204): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:3204): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:3204): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:3204): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:3204): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:3204): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:3204): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:3204): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:3204): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:3204): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:3204): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:3204): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:3204): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:3204): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:3204): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:3204): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:3204): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:3204): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:3204): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:3204): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:3204): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:3204): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:3204): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:3204): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:3204): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:3204): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:3204): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:3204): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:3204): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:3204): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:3204): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:3204): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
** (<unknown>:3204): DEBUG: IndicatorAdded: libapplication.so
** (<unknown>:3204): DEBUG: IndicatorAdded: libsoundmenu.so
** (<unknown>:3204): DEBUG: IndicatorAdded: libmessaging.so
** (<unknown>:3204): DEBUG: IndicatorAdded: libdatetime.so
** (<unknown>:3204): DEBUG: IndicatorAdded: libme.so
** (<unknown>:3204): DEBUG: IndicatorAdded: libsession.so
Setting Update "run_command_terminal_key"
Setting Update "fullscreen_visual_bell"

** (<unknown>:3204): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window58720324: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:3204): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window58720324: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:3204): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



** (<unknown>:3204): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:3204): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:3204): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:3204): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:3204): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:3204): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:3204): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (<unknown>:3204): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window67108869: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:3204): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window67108869: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:3204): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:3204): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:3204): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:3204): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `BamfView'

** (<unknown>:3204): CRITICAL **: bamf_view_get_children: assertion `BAMF_IS_VIEW (view)' failed

(<unknown>:3204): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(<unknown>:3204): GLib-GObject-CRITICAL **: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed

(<unknown>:3204): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:3204): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:3204): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:3204): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:3204): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:3204): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:3204): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:3204): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:3204): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:3204): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:3204): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:3204): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:3204): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:3204): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:3204): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:3204): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:3204): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:3204): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:3204): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** (<unknown>:3204): DEBUG: MaximizeIfBigEnough: Gnome-terminal window size doesn't fit

(<unknown>:3204): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:3204): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
** (<unknown>:3204): DEBUG: MaximizeIfBigEnough: Gedit window size doesn't fit
```

Please let me know if you need more information. I'm happy to provide them.

Cheers,
3ar1

---

### Post by 3ar1 on 2011-05-15
Ok, I've found out evolution causes metacity to freeze as well if I click any contact in the address book. After killing evolution everything works fine again. So there's actually two problems: 1) Why is evolution's address book not working for me? 2) Why can both metacity and unity freeze if an application is crashing?

---

### Post by Nausser on 2011-05-16
I have a similar issue on two different laptops running 11.04 with the Unity desktop. The first is an HP netbook with a clean install. The second is my own laptop which is an Acer that I've been using Ubuntu as my only OS since 8.04. It was an upgrade from 10.10.

I do not have to do anything special on either machine to have Evolution crash my Unity desktop. On my own Acer laptop, I never even get to see the email program. The only things I can click on are the "File Edit View etc...." at the top when I hover my mouse. I then can go to File > Quit/Close to terminate the program. When the Evolution email program is in focus, it absolutely locks up the entire desktop and makes the pop out program menu on the left of the screen grind to a near halt.

It seems puzzling to me how a desktop change (one that I favor), can cause an email program not to function. This certainly needs to be resolved soon. Email communication is of top importance and I am dead in the water right now with exception to my phone which isn't too great for responding to many emails in a short and efficient amount of time.

I know I could be supplying more details of my install. I thought it was a fluke incident with the HP net book. Now that I know the issue is even worse on my computer, I would have to guess it isn't machine related so much as a bug in the software that has been introduced. Please let me know of any reports or other information that would be helpful to expedite the solution to this issue. I don't have constant access to the HP net book, only my own Acer laptop.

Here is a desktop video of the symptoms described above.
[http://nerdsonstandby.com/dwnlds/Video/evolution_U11.04_Hang.ogv]("http://nerdsonstandby.com/dwnlds/Video/evolution_U11.04_Hang.ogv")

Thank you.

---

### Post by 3ar1 on 2011-05-16
Hi Nausser,

so we're at least two guys having this problem. I'm running Ubuntu (64bit) on an Acer notebook, too. I'll file a bug report on evolution's project page as soon as I have some time available for that. I'll keep you posted!

Cheers,
3ar1

---

### Post by NormanFLinux on 2011-05-16
Workaround is to refrain from running evolution until an update can be posted to make it compatible with Natty.

---

### Post by wildmanne39 on 2011-05-16
> **NormanFLinux said:**
> Workaround is to refrain from running evolution until an update can be posted to make it compatible with Natty.

Hi, the only time I had a problem with crashing was when I upgraded, I had to do a fresh install, and right after I had to use the 173 nvidia driver for my graphics card not the current one. But it is working great, also you can not enable any effect in compiz when running unity, if you want compiz you need to log out and hit your user name and go to the bottom of the screen and click ubuntu classic and you can enable effects, I am running the cube and full effects in classic mode no problem at all.:D

---

### Post by 3ar1 on 2011-05-18
I've filed a [bug report]("https://bugzilla.gnome.org/show_bug.cgi?id=650492").

---

