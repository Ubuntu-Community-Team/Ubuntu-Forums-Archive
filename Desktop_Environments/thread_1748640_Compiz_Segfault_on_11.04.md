---
title: "Compiz Segfault on 11.04"
date: 2011-05-03
forum: Desktop Environments
---

### Post by castironpants on 2011-05-03
I keep getting a segfault in compiz. I've tried everything! This is from a fresh install without and accelerated drivers (I have ATI)


> ```
**Switching to Compiz window management**
/usr/local/bin/compiz-indicator:99: GtkWarning: Can't set a parent on widget which has a parent

  menu.append(kill)
/usr/local/bin/compiz-indicator:100: GtkWarning: Can't set a parent on widget which has a parent

  menu.append(start)
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
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
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
** (<unknown>:29030): DEBUG: Unity accessibility initialization
** (<unknown>:29030): DEBUG: Shows on edge: 1

Screen geometry changed:
  Monitor 0(primary)
   0x0x1366x768

** (<unknown>:29030): DEBUG: PanelController:: Added Panel for Monitor 0
Initializing unityshell options...done
** (<unknown>:29030): DEBUG: MaximizeIfBigEnough: Gnome-terminal window size doesn't fit
** (<unknown>:29030): DEBUG: PlaceEntry: Applications
** (<unknown>:29030): DEBUG: PlaceEntry: Commands
** (<unknown>:29030): DEBUG: PlaceEntry: Files & Folders
** (<unknown>:29030): DEBUG: /com/canonical/unity/applicationsplace
** (<unknown>:29030): DEBUG: /com/canonical/unity/filesplace
** (<unknown>:29030): DEBUG: Setting to primary screen rect: x=0 y=0 w=1366 h=768

(<unknown>:29030): GLib-GIO-CRITICAL **: g_dbus_connection_call_finish: assertion `G_IS_DBUS_CONNECTION (connection)' failed

** (<unknown>:29030): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window81790238: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


(<unknown>:29030): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

** (<unknown>:29030): CRITICAL **: bamf_view_is_sticky: assertion `BAMF_IS_VIEW (view)' failed

** (<unknown>:29030): WARNING **: Failed to fetch view type at /org/ayatana/bamf/application311805604: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


(<unknown>:29030): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

** (<unknown>:29030): CRITICAL **: bamf_view_is_sticky: assertion `BAMF_IS_VIEW (view)' failed

** (<unknown>:29030): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window48234498: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


(<unknown>:29030): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

** (<unknown>:29030): CRITICAL **: bamf_view_is_sticky: assertion `BAMF_IS_VIEW (view)' failed

** (<unknown>:29030): WARNING **: Failed to fetch view type at /org/ayatana/bamf/application0x91a9ea8: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


(<unknown>:29030): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

** (<unknown>:29030): CRITICAL **: bamf_view_is_sticky: assertion `BAMF_IS_VIEW (view)' failed

** (<unknown>:29030): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window48234497: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


(<unknown>:29030): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

** (<unknown>:29030): CRITICAL **: bamf_view_is_sticky: assertion `BAMF_IS_VIEW (view)' failed

** (<unknown>:29030): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window48234497: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:29030): WARNING **: Failed to fetch view type at /org/ayatana/bamf/application0x91a9ea8: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:29030): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window48234498: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:29030): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window48234497: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:29030): WARNING **: Failed to fetch view type at /org/ayatana/bamf/application0x91a9ea8: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:29030): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window81790238: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:29030): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window79691845: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:29030): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window79691845: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:29030): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window69206017: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:29030): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window54525953: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:29030): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window52428801: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:29030): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window77594625: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:29030): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window67108865: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:29030): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window50331649: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:29030): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window29360170: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:29030): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window29412276: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:29030): WARNING **: Failed to fetch view type at /org/ayatana/bamf/application0x91a9ea8: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:29030): WARNING **: Failed to fetch view type at /org/ayatana/bamf/application311805604: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:29030): WARNING **: Failed to fetch view type at /org/ayatana/bamf/application0x91a9f08: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:29030): WARNING **: Failed to fetch view type at /org/ayatana/bamf/application829906520: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

Segmentation fault

```

---

### Post by haudace on 2011-05-04
Same problem dude/tte, something is really wrong with bamfview class. I wonder what I did to break it, but I don't think I'm at fault here. I also have an ati card. I will keep following this thread to see if anyone comes up with a solution.

---

### Post by afrodeity on 2011-05-22
> **haudace said:**
> Same problem dude/tte, something is really wrong with bamfview class. I wonder what I did to break it, but I don't think I'm at fault here. I also have an ati card. I will keep following this thread to see if anyone comes up with a solution.

```

compiz[22571]: segfault at f ip 0018f33d sp bfacddf4 error 4 in libpthread-2.13.so[187000+15000]

```

I have this in my kernel log.

---

### Post by Alexis Wilke on 2011-10-03
Same here... twice in a raw. Then I don't get the gnome-panel started (or my sessions if that matter.)

I just upgraded from 10.10 to 11.04 and cannot really use my X session without starting gnome-panel manually (I have an icon on the desktop to start a terminal.)

Oct  3 01:54:40 XXX kernel: [ 5041.702338] compiz[15339]: segfault at 0 ip 0000000040447fa8 sp 00007fffd1cdc3e8 error 4 in gl94PyVP (deleted)[40446000+2000]
Oct  3 01:54:40 XXX kernel: [ 5042.035564] compiz[15397]: segfault at 0 ip 00000000409bcfa8 sp 00007fffe41a40b8 error 4 in glZ7Gjye (deleted)[409bb000+2000]

See also: [http://ubuntuforums.org/showthread.php?t=1751407](http://ubuntuforums.org/showthread.php?t=1751407)

---

