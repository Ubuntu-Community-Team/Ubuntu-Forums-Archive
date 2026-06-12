---
title: "Constant Screen Crashes in 11.04!"
date: 2011-05-01
forum: Desktop Environments
---

### Post by castironpants on 2011-05-01
[Here's the YouTube video of the error in action]("http://www.youtube.com/watch?v=FZQMa7gLqkg")

I just upgraded from 10.10 to 11.04 and am using the "Classic" GNOME 2 interface. I have an ATI card, currently powered by the standard fglrx drivers. Something must be wrong with compositing, because when I mouse over Avant Window Navigator, indicators, menus, drag files, etc, there is a good (but still random) chance of it breaking my display.

Just for the record, I have tried this with the newest Catalyst drivers from the official website, the fglrx drivers from the repository and without any fglrx drivers at all. I am running a patched version of Emerald that works with the included compiz, but I still get the same crashes with Metacity's window decorator and without Avant Window Navigator. Indicator menus will just crash the screen from gnome-panel.

I had also gotten this same problem in a previous Natty install using Unity. I know that a video isn't enough to diagnose the problem, but I don't know which logs would be helpful to include, so please let me know what I can do to help.


**EDIT:** Hmm, disabling Compiz seems to keep the crashes at bay, so I think this is a (major) compiz bug. Does anyone know which logs I should include in my bug report?

---

### Post by castironpants on 2011-05-01
I got this:

Loaded symbols for /usr/lib/libGLU.so.1
0xb78a9424 in __kernel_vsyscall ()
(gdb) (gdb) 
Thread 2 (Thread 0xb6d68b70 (LWP 31128)):
#0  0xb78a9424 in __kernel_vsyscall ()
#1  0xb70b3f76 in poll () from /lib/i386-linux-gnu/libc.so.6
#2  0xb736384b in g_poll (fds=0x8343bd8, nfds=1, timeout=-1) at /build/buildd/glib2.0-2.28.6/./glib/gpoll.c:132
No locals.
#3  0xb73531af in g_main_context_poll (context=0x8340dd0, block=-1221183456, dispatch=1, self=<value optimized out>) at /build/buildd/glib2.0-2.28.6/./glib/gmain.c:3404
        poll_func = 0xb7363820 <g_poll>
#4  g_main_context_iterate (context=0x8340dd0, block=-1221183456, dispatch=1, self=<value optimized out>) at /build/buildd/glib2.0-2.28.6/./glib/gmain.c:3086
        max_priority = 2147483647
        timeout = -1
        some_ready = <value optimized out>
        nfds = 1
        allocated_nfds = <value optimized out>
        fds = 0x8343bd8
#5  0xb735392b in g_main_loop_run (loop=0x8340dc0) at /build/buildd/glib2.0-2.28.6/./glib/gmain.c:3299
        __PRETTY_FUNCTION__ = "g_main_loop_run"
#6  0xb7563304 in gdbus_shared_thread_func (data=0x0) at /build/buildd/glib2.0-2.28.6/./gio/gdbusprivate.c:276
No locals.
#7  0xb737c2df in g_thread_create_proxy (data=0x8340e60) at /build/buildd/glib2.0-2.28.6/./glib/gthread.c:1897
        thread = 0x8340e60
        __PRETTY_FUNCTION__ = "g_thread_create_proxy"
#8  0xb728ae99 in start_thread () from /lib/i386-linux-gnu/libpthread.so.0
#9  0xb70c273e in clone () from /lib/i386-linux-gnu/libc.so.6

Thread 1 (Thread 0xb6f43760 (LWP 31126)):
#0  0xb78a9424 in __kernel_vsyscall ()
#1  0xb708aaeb in waitpid () from /lib/i386-linux-gnu/libc.so.6
#2  0xb702b513 in ?? () from /lib/i386-linux-gnu/libc.so.6
#3  0xb702b9ca in system () from /lib/i386-linux-gnu/libc.so.6
#4  0xb72938ed in system () from /lib/i386-linux-gnu/libpthread.so.0
#5  0xb6dfc4cb in ?? () from /usr/lib/compiz/libcrashhandler.so
#6  <signal handler called>
#7  0xb705ed5d in ?? () from /lib/i386-linux-gnu/libc.so.6
#8  0xb706241d in free () from /lib/i386-linux-gnu/libc.so.6
#9  0xb5c8360b in ?? () from /usr/lib/fglrx/dri/fglrx_dri.so
#10 0xb5d637b8 in ?? () from /usr/lib/fglrx/dri/fglrx_dri.so
#11 0xb536a650 in ?? () from /usr/lib/fglrx/dri/fglrx_dri.so
Backtrace stopped: previous frame inner to this frame (corrupt stack?)
(gdb) 
(gdb) 
(gdb) #0  0xb78a9424 in __kernel_vsyscall ()
#1  0xb708aaeb in waitpid () from /lib/i386-linux-gnu/libc.so.6
#2  0xb702b513 in ?? () from /lib/i386-linux-gnu/libc.so.6
#3  0xb702b9ca in system () from /lib/i386-linux-gnu/libc.so.6
#4  0xb72938ed in system () from /lib/i386-linux-gnu/libpthread.so.0
#5  0xb6dfc4cb in ?? () from /usr/lib/compiz/libcrashhandler.so
#6  <signal handler called>
#7  0xb705ed5d in ?? () from /lib/i386-linux-gnu/libc.so.6
#8  0xb706241d in free () from /lib/i386-linux-gnu/libc.so.6
#9  0xb5c8360b in ?? () from /usr/lib/fglrx/dri/fglrx_dri.so
#10 0xb5d637b8 in ?? () from /usr/lib/fglrx/dri/fglrx_dri.so
#11 0xb536a650 in ?? () from /usr/lib/fglrx/dri/fglrx_dri.so
Backtrace stopped: previous frame inner to this frame (corrupt stack?)
(gdb) A debugging session is active.

	Inferior 1 [process 31126] will be detached.

Quit anyway? (y or n) [answered Y; input not from terminal]
Detaching from program: /usr/bin/compiz, process 31126

---

### Post by SantaFe on 2011-05-01
Don't know if it's related, but am also using an ATI card, an Radeon X300, and while the screen doesn't crash, big sections of my panel both bottom & top will suddenly go transparent.  Does it in either Ubuntu classic, or Ubuntu Classic (no effects).  Weird.  KDE & Xfce have no problems.

---

### Post by cespinal on 2011-05-02
+1 here.... screen crashes and then the system goes unresponsive. I can move the mouse and the system still runs but nothing else.

---

### Post by iamnotthemessiah on 2011-05-02
had this problem, identified it as settings certain apps such as gdeskcal to not have shadows in ccsm > window decoration > shadow. setting it back to 'any' (without the '') and problems gone

---

### Post by castironpants on 2011-05-02
Won't fix mine, it was crashing on the default Compiz install with any in both decorate and shadow

---

### Post by cespinal on 2011-05-03
me neither.. my settings were on "any" already

so shameless bump

---

### Post by castironpants on 2011-05-03
I filed this bug report

[http://bugs.opencompositing.org/show_bug.cgi?id=1339](http://bugs.opencompositing.org/show_bug.cgi?id=1339)

So go there and make a lot of fuss and maybe they'll take care of it sooner

---

### Post by castironpants on 2011-05-03
I did a complete reinstall, and I'm not even using accelerated drivers, and it's still crashing. But this time I managed to copy part of the log that included a segfault.


```
`BAMF_IS_APPLICATION (application)' failed

(<unknown>:21495): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:21495): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:21495): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:21495): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:21495): GLib-GIO-CRITICAL **: g_dbus_connection_register_object: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed

(<unknown>:21495): GLib-GIO-CRITICAL **: g_dbus_connection_register_object: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed
[jeremy: /usr/local/bin]$ ** (<unknown>:21495): DEBUG: IndicatorAdded: libapplication.so
** (<unknown>:21495): DEBUG: IndicatorAdded: libsoundmenu.so
** (<unknown>:21495): DEBUG: IndicatorAdded: libmessaging.so
** (<unknown>:21495): DEBUG: IndicatorAdded: libdatetime.so
** (<unknown>:21495): DEBUG: IndicatorAdded: libme.so
** (<unknown>:21495): DEBUG: IndicatorAdded: libsession.so
Setting Update "shadow_match"
Setting Update "command0"
Setting Update "command1"
Setting Update "command2"
Setting Update "run_command0_key"
Setting Update "run_command1_key"
Setting Update "directory"
Setting Update "start_wm"
Setting Update "wm_cmd"
Setting Update "run_command_window_screenshot_key"
Setting Update "run_command_terminal_key"
Setting Update "unfold_key"
Setting Update "top_color"
Setting Update "bottom_color"
Setting Update "skydome"
Setting Update "skydome_image"
Setting Update "skydome_animated"
Setting Update "top_next_key"
Setting Update "reflection"
Setting Update "unfold_deformation"
Setting Update "cylinder_manual_only"
Setting Update "top_images"
Setting Update "bottom_images"
Setting Update "expo_key"
Setting Update "deform"
Setting Update "show_launcher"
Setting Update "backlight_mode"
Setting Update "panel_opacity"

** (<unknown>:21495): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window20974941: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:21495): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window20974941: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

[jeremy: /usr/local/bin]$ /usr/local/bin/compiz.start: line 2: 21495 Segmentation fault      compiz --replace
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
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing titleinfo options...done
Initializing commands options...done
Initializing animation options...done
Initializing animationaddon options...done
Initializing move options...done
Initializing crashhandler options...done
Initializing gnomecompat options...done
Initializing imgjpeg options...done
Initializing mousepoll options...done
Initializing resize options...done
Initializing wobbly options...done
Initializing cube options...done
Initializing place options...done
Initializing imgsvg options...done
Initializing td options...done
Initializing rotate options...done
Initializing cubeaddon options...done
Initializing expo options...done
** (<unknown>:21599): DEBUG: Unity accessibility initialization
** (<unknown>:21599): DEBUG: Shows on edge: 1

Screen geometry changed:
  Monitor 0(primary)
   0x0x1366x768

** (<unknown>:21599): DEBUG: PanelController:: Added Panel for Monitor 0
Initializing unityshell options...done
[jeremy: /usr/local/bin]$ ** (<unknown>:21599): DEBUG: MaximizeIfBigEnough: Gnome-terminal window size doesn't fit
[jeremy: /usr/local/bin]$ ** (<unknown>:21599): DEBUG: PlaceEntry: Applications
** (<unknown>:21599): DEBUG: PlaceEntry: Commands
** (<unknown>:21599): DEBUG: PlaceEntry: Files & Folders
** (<unknown>:21599): DEBUG: /com/canonical/unity/applicationsplace
** (<unknown>:21599): DEBUG: /com/canonical/unity/filesplace
** (<unknown>:21599): DEBUG: Setting to primary screen rect: x=0 y=0 w=1366 h=768

** (<unknown>:21599): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window48246987: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


(<unknown>:21599): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:21599): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:21599): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:21599): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

** (<unknown>:21599): WARNING **: Failed to fetch view type at /org/ayatana/bamf/application0x91a9d88: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

** (<unknown>:21599): DEBUG: Acquired the name com.canonical.Unity.Launcher on the session bus


** (<unknown>:21599): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window48246987: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:21599): WARNING **: Failed to fetch view type at /org/ayatana/bamf/application0x91a9d88: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:21599): WARNING **: Failed to fetch view type at /org/ayatana/bamf/application0x91a9d88: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

** (<unknown>:21599): DEBUG: TrayChild Rejected: Sound Output Volume gnome-volume-control-applet Gnome-volume-control-applet
[jeremy: /usr/local/bin]$ ** (<unknown>:21599): DEBUG: IndicatorAdded: libapplication.so
** (<unknown>:21599): DEBUG: IndicatorAdded: libsoundmenu.so
** (<unknown>:21599): DEBUG: IndicatorAdded: libmessaging.so
** (<unknown>:21599): DEBUG: IndicatorAdded: libdatetime.so
** (<unknown>:21599): DEBUG: IndicatorAdded: libme.so
** (<unknown>:21599): DEBUG: IndicatorAdded: libsession.so
Setting Update "shadow_match"
Setting Update "command0"
Setting Update "command1"
Setting Update "command2"
Setting Update "run_command0_key"
Setting Update "run_command1_key"
Setting Update "directory"
Setting Update "start_wm"
Setting Update "wm_cmd"
Setting Update "run_command_window_screenshot_key"
Setting Update "run_command_terminal_key"
Setting Update "unfold_key"
Setting Update "top_color"
Setting Update "bottom_color"
Setting Update "skydome"
Setting Update "skydome_image"
Setting Update "skydome_animated"
Setting Update "top_next_key"
Setting Update "reflection"
Setting Update "unfold_deformation"
Setting Update "cylinder_manual_only"
Setting Update "top_images"
Setting Update "bottom_images"
Setting Update "expo_key"
Setting Update "deform"
Setting Update "show_launcher"
Setting Update "backlight_mode"
Setting Update "panel_opacity"
/usr/local/bin/compiz.start: line 2: 21599 Segmentation fault      compiz --replace
[jeremy: /usr/local/bin]$ Backend     : gconf
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
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing titleinfo options...done
Initializing commands options...done
Initializing animation options...done
Initializing animationaddon options...done
Initializing move options...done
Initializing crashhandler options...done
Initializing gnomecompat options...done
Initializing imgjpeg options...done
Initializing mousepoll options...done
Initializing resize options...done
Initializing wobbly options...done
Initializing cube options...done
Initializing place options...done
Initializing imgsvg options...done
Initializing td options...done
Initializing rotate options...done
Initializing cubeaddon options...done
Initializing expo options...done
** (<unknown>:21637): DEBUG: Unity accessibility initialization
** (<unknown>:21637): DEBUG: Shows on edge: 1

Screen geometry changed:
  Monitor 0(primary)
   0x0x1366x768

unity-panel-service: no process found
** (<unknown>:21637): DEBUG: PanelController:: Added Panel for Monitor 0
Initializing unityshell options...done
[jeremy: /usr/local/bin]$ ** (<unknown>:21637): DEBUG: MaximizeIfBigEnough: Gnome-terminal window size doesn't fit
[jeremy: /usr/local/bin]$ ** (<unknown>:21637): DEBUG: PlaceEntry: Applications
** (<unknown>:21637): DEBUG: PlaceEntry: Commands
** (<unknown>:21637): DEBUG: PlaceEntry: Files & Folders
** (<unknown>:21637): DEBUG: /com/canonical/unity/applicationsplace
** (<unknown>:21637): DEBUG: /com/canonical/unity/filesplace
** (<unknown>:21637): DEBUG: Setting to primary screen rect: x=0 y=0 w=1366 h=768
** (<unknown>:21637): DEBUG: Acquired the name com.canonical.Unity.Launcher on the session bus


** (<unknown>:21637): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window48248464: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:21637): WARNING **: Failed to fetch view type at /org/ayatana/bamf/application0x91a9c68: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:21637): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window48248464: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:21637): WARNING **: Failed to fetch view type at /org/ayatana/bamf/application0x91a9c68: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:21637): WARNING **: Failed to fetch view type at /org/ayatana/bamf/application0x91a9c68: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

** (<unknown>:21637): DEBUG: TrayChild Rejected: Sound Output Volume gnome-volume-control-applet Gnome-volume-control-applet

(<unknown>:21637): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:21637): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:21637): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:21637): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:21637): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:21637): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:21637): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:21637): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:21637): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:21637): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:21637): GLib-GIO-CRITICAL **: g_bus_own_name: assertion `g_dbus_is_name (name) && !g_dbus_is_unique_name (name)' failed

(<unknown>:21637): GLib-GIO-CRITICAL **: g_bus_watch_name: assertion `g_dbus_is_name (name)' failed

(<unknown>:21637): GLib-GIO-CRITICAL **: g_bus_own_name: assertion `g_dbus_is_name (name) && !g_dbus_is_unique_name (name)' failed

(<unknown>:21637): GLib-GIO-CRITICAL **: g_bus_watch_name: assertion `g_dbus_is_name (name)' failed
** (<unknown>:21637): DEBUG: Connected to proxy
** (<unknown>:21637): DEBUG: Connected to proxy
** (<unknown>:21637): DEBUG: Connected to proxy

(<unknown>:21637): GLib-GIO-CRITICAL **: g_dbus_connection_register_object: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed

(<unknown>:21637): GLib-GIO-CRITICAL **: g_dbus_connection_register_object: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed
[jeremy: /usr/local/bin]$ ** (<unknown>:21637): DEBUG: IndicatorAdded: libapplication.so
** (<unknown>:21637): DEBUG: IndicatorAdded: libsoundmenu.so
** (<unknown>:21637): DEBUG: IndicatorAdded: libmessaging.so
** (<unknown>:21637): DEBUG: IndicatorAdded: libdatetime.so
** (<unknown>:21637): DEBUG: IndicatorAdded: libme.so
** (<unknown>:21637): DEBUG: IndicatorAdded: libsession.so
Setting Update "shadow_match"
Setting Update "command0"
Setting Update "command1"
Setting Update "command2"
Setting Update "run_command0_key"
Setting Update "run_command1_key"
Setting Update "directory"
Setting Update "start_wm"
Setting Update "wm_cmd"
Setting Update "run_command_window_screenshot_key"
Setting Update "run_command_terminal_key"
Setting Update "unfold_key"
Setting Update "top_color"
Setting Update "bottom_color"
Setting Update "skydome"
Setting Update "skydome_image"
Setting Update "skydome_animated"
Setting Update "top_next_key"
Setting Update "reflection"
Setting Update "unfold_deformation"
Setting Update "cylinder_manual_only"
Setting Update "top_images"
Setting Update "bottom_images"
Setting Update "expo_key"
Setting Update "deform"
Setting Update "show_launcher"
Setting Update "backlight_mode"
Setting Update "panel_opacity"


```

---

### Post by PatrickVogeli on 2011-05-06
same here...

---

### Post by cespinal on 2011-05-06
My screen crashes are gone after some updates...

---

### Post by tareed on 2011-05-06
I removed all of the indicator-appmenu packages and that solved the problem for me. The crashes always seemed to happen with I interacted with the global menu.

I'll re-install them to see if the bug has been fixed.

---

### Post by castironpants on 2011-05-06
I think in all likelihood this is a much larger problem with compiz. It seems to happen either A) when there's any compositing (including Avant Window Navigator) B) indicators/menus C) randomly.

---

### Post by Antarctica32 on 2011-05-06
I have seen this before with unity. I had it on a laptop once with ubuntu netbook (which uses unity all the same). After about a month I figured that the GPU just couldn't handle unity. I did hear of a fix however for it about last week. The thing is sometimes everything will just work fine when you go into gnome and it only does it in unity. However, sometimes it does it both with gnome and unity

---

