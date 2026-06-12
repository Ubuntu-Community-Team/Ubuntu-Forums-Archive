---
title: "Compiz on 11.4 classic-gnome session doesn't work..."
date: 2011-05-01
forum: Desktop Environments
---

### Post by azupan on 2011-05-01
... and neither does OpenGL version of Cairo Docs. I presume, that OpenGL is the problem.

I use NVIDIA drivers.

BTW, the reason why I'm still playing with classic gnome:

[LIST]
[*]I'm used to it
[*]No way of customizing dash. I use webmail, and I have no photos on my computer, thank you.
[*]No way of hiding top panel. OK, I know, top panel auto hiding in Unity doesn't seem logical at the first glance, **but**:
[LIST]
[*]On today's wide screen monitors, it makes sense to keep non-maximized windows side by side. In this case, the top panel just takes up valuable vertical space
[*]Many applications are not integrated into unity, in my case Netbeans. When Netbeans is maximized, it's main menu does not migrate into the top panel.
[/LIST]
 
[/LIST]

---

### Post by azupan on 2011-05-02
I experimented googled around a little bit, and found no useful answers.

Are desktop effects in 11.4 classic ubuntu supposed to work at all? At a first glance, everything looks kinda disabled- Compiz, as well as OpenGL Cairo Dock.

---

### Post by Krytarik on 2011-05-02
Try disabling "Sync to VBlank" in "CompizConfig Settings Manager -> OpenGL".
If you don't have CCSM already installed, "compizconfig-settings-manager" is in the official repos.

Greetings.

---

### Post by azupan on 2011-05-02
> **Krytarik said:**
> Try disabling "Sync to VBlank" in "CompizConfig Settings Manager -> OpenGL".
If you don't have CCSM already installed, "compizconfig-settings-manager" is in the official repos.

Greetings.

It didn't helped. Things I've tried so far, among others:


[LIST]
[*]Uninstall Nvida driver, install experimental open source 3d driver. It didn't work, and I installed Nvidia again.
[*]Fiddle around /usr/share/xsessions, to no avail, of course. I did that, because I noticed that both Ubuntu Classic, and Ubuntu Classic without effect sessions behave the same.
[/LIST]
Using Configuration Editor I noticed, that there are two sets od Compiz settings in my machine: /apps/compiz, and /apps/compiz-1. My old settings before upgrade to 11.4 are stored in /apps/compiz, new settings in /apps/compiz-1.

---

### Post by Krytarik on 2011-05-02
Ah, now it seems like you meant your earlier note literally, then check if Compiz is running at all:
```
ps ax |grep -v grep |grep compiz
```If it's not, press Alt+F2 and enter:
```
compiz --replace
```If you want/need to reset all Compiz settings, run:
```
gconftool-2 --recursive-unset /apps/compiz
gconftool-2 --recursive-unset /apps/compiz-1
```Of course, Compiz shouldn't be running at that time.

---

### Post by azupan on 2011-05-02
Compiz indeed wasn't running, and when I started it in terminal by compiz --replace, it started to work.

But... lo and behold, Unity launcher and top panel appeared all of the sudden... why, of course, Unity plugin is enabled. So, let's disable it... awww, bummer, menus from all windows disappeared! Ummm..., yeah, that makes sense too. Individual window menus are supposed to be displayed by Unity. Guess that's why Classic Ubuntu session doesn't run Compiz.

OK, now that I have the basic idea about what's going on, I think I can handle myself from now on. Thanks for the help! :)

If I manage to figure out a workable solution, I'll post it here. Starting compiz with the old settings or something could help, I think.


Here's output from the compiz --replace command, in case anybody at Canonical is interested (I'm new here, and don't know where to post this stuff):

```

drejc@drejc4-Ubuntu:~$ compiz --replace
Backend     : gconf
Integration : true
Profile     : default
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
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
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
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing imgjpeg options...[ERROR]: Option "quality" already defined
done
Initializing decor options...done
Initializing resize options...done
Initializing gnomecompat options...done
Initializing place options...done
Initializing mousepoll options...done
compiz (core) - Error: Plugin 'text' not loaded.

compiz (shift) - Warn: No compatible text plugin loaded
Initializing shift options...[ERROR]: Option "initiate_key" already defined
[ERROR]: Option "initiate_button" already defined
[ERROR]: Option "initiate_edge" already defined
[ERROR]: Option "initiate_all_key" already defined
[ERROR]: Option "initiate_all_button" already defined
[ERROR]: Option "initiate_all_edge" already defined
[ERROR]: Option "terminate_button" already defined
[ERROR]: Option "next_key" already defined
[ERROR]: Option "next_button" already defined
[ERROR]: Option "prev_key" already defined
[ERROR]: Option "prev_button" already defined
[ERROR]: Option "next_all_key" already defined
[ERROR]: Option "next_all_button" already defined
[ERROR]: Option "prev_all_key" already defined
[ERROR]: Option "prev_all_button" already defined
[ERROR]: Option "next_group_key" already defined
[ERROR]: Option "next_group_button" already defined
[ERROR]: Option "prev_group_key" already defined
[ERROR]: Option "prev_group_button" already defined
[ERROR]: Option "speed" already defined
[ERROR]: Option "shift_speed" already defined
[ERROR]: Option "timestep" already defined
[ERROR]: Option "window_match" already defined
[ERROR]: Option "minimized" already defined
[ERROR]: Option "mouse_speed" already defined
[ERROR]: Option "click_duration" already defined
[ERROR]: Option "mode" already defined
[ERROR]: Option "size" already defined
[ERROR]: Option "background_intensity" already defined
[ERROR]: Option "hide_all" already defined
[ERROR]: Option "reflection" already defined
[ERROR]: Option "ground_color1" already defined
[ERROR]: Option "ground_color2" already defined
[ERROR]: Option "ground_size" already defined
[ERROR]: Option "intensity" already defined
[ERROR]: Option "flip_rotation" already defined
[ERROR]: Option "cover_offset" already defined
[ERROR]: Option "cover_angle" already defined
[ERROR]: Option "cover_extra_space" already defined
[ERROR]: Option "cover_max_visible_windows" already defined
[ERROR]: Option "overlay_icon" already defined
[ERROR]: Option "mipmaps" already defined
[ERROR]: Option "multioutput_mode" already defined
[ERROR]: Option "window_title" already defined
[ERROR]: Option "title_font_bold" already defined
[ERROR]: Option "title_font_size" already defined
[ERROR]: Option "title_back_color" already defined
[ERROR]: Option "title_font_color" already defined
[ERROR]: Option "title_text_placement" already defined
done
Initializing fadedesktop options...[ERROR]: Option "fadetime" already defined
[ERROR]: Option "window_match" already defined
done
Initializing grid options...done
Initializing water options...[ERROR]: Option "initiate_key" already defined
[ERROR]: Option "toggle_rain_key" already defined
[ERROR]: Option "toggle_wiper_key" already defined
[ERROR]: Option "offset_scale" already defined
[ERROR]: Option "rain_delay" already defined
[ERROR]: Option "title_wave" already defined
[ERROR]: Option "point" already defined
[ERROR]: Option "line" already defined
done
Initializing move options...done
Initializing wobbly options...done
Initializing fade options...done
Initializing cube options...done
Initializing td options...done
Initializing rotate options...done
Initializing cubeaddon options...[ERROR]: Option "top_next_key" already defined
[ERROR]: Option "top_next_button" already defined
[ERROR]: Option "top_prev_key" already defined
[ERROR]: Option "top_prev_button" already defined
[ERROR]: Option "bottom_next_key" already defined
[ERROR]: Option "bottom_next_button" already defined
[ERROR]: Option "bottom_prev_key" already defined
[ERROR]: Option "bottom_prev_button" already defined
[ERROR]: Option "reflection" already defined
[ERROR]: Option "ground_color1" already defined
[ERROR]: Option "ground_color2" already defined
[ERROR]: Option "ground_size" already defined
[ERROR]: Option "intensity" already defined
[ERROR]: Option "auto_zoom" already defined
[ERROR]: Option "zoom_manual_only" already defined
[ERROR]: Option "mode" already defined
[ERROR]: Option "deformation" already defined
[ERROR]: Option "unfold_deformation" already defined
[ERROR]: Option "cylinder_manual_only" already defined
[ERROR]: Option "deform_caps" already defined
[ERROR]: Option "sphere_aspect" already defined
[ERROR]: Option "draw_top" already defined
[ERROR]: Option "draw_bottom" already defined
[ERROR]: Option "adjust_top" already defined
[ERROR]: Option "adjust_bottom" already defined
[ERROR]: Option "top_scale" already defined
[ERROR]: Option "bottom_scale" already defined
[ERROR]: Option "top_aspect" already defined
[ERROR]: Option "bottom_aspect" already defined
[ERROR]: Option "top_clamp" already defined
[ERROR]: Option "bottom_clamp" already defined
[ERROR]: Option "top_images" already defined
[ERROR]: Option "bottom_images" already defined
done
Initializing expo options...done
** (<unknown>:15447): DEBUG: Unity accessibility initialization
** (<unknown>:15447): DEBUG: Shows on edge: 1

Screen geometry changed:
  Monitor 0(primary)
   0x0x1920x1200
  Monitor 1
   1920x0x1920x1200

unity-panel-service: no process found
** (<unknown>:15447): DEBUG: PanelController:: Added Panel for Monitor 0
unity-panel-service: no process found
** (<unknown>:15447): DEBUG: PanelController:: Added Panel for Monitor 1
Initializing unityshell options...done
** (<unknown>:15447): DEBUG: MaximizeIfBigEnough: Gnome-terminal window size doesn't fit
** (<unknown>:15447): DEBUG: PlaceEntry: Applications
** (<unknown>:15447): DEBUG: PlaceEntry: Commands
** (<unknown>:15447): DEBUG: PlaceEntry: Files & Folders
** (<unknown>:15447): DEBUG: /com/canonical/unity/applicationsplace
** (<unknown>:15447): DEBUG: /com/canonical/unity/filesplace
** (<unknown>:15447): DEBUG: Setting to primary screen rect: x=0 y=0 w=1920 h=1200
** (<unknown>:15447): DEBUG: Acquired the name com.canonical.Unity.Launcher on the session bus

** (<unknown>:15447): DEBUG: Connected to proxy

(<unknown>:15447): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** (<unknown>:15447): DEBUG: Connected to proxy
** (<unknown>:15447): DEBUG: Connected to proxy

(<unknown>:15447): GLib-GIO-CRITICAL **: g_bus_own_name: assertion `g_dbus_is_name (name) && !g_dbus_is_unique_name (name)' failed

(<unknown>:15447): GLib-GIO-CRITICAL **: g_bus_watch_name: assertion `g_dbus_is_name (name)' failed

(<unknown>:15447): GLib-GIO-CRITICAL **: g_bus_own_name: assertion `g_dbus_is_name (name) && !g_dbus_is_unique_name (name)' failed

(<unknown>:15447): GLib-GIO-CRITICAL **: g_bus_watch_name: assertion `g_dbus_is_name (name)' failed

(<unknown>:15447): GLib-GIO-CRITICAL **: g_dbus_connection_register_object: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed

(<unknown>:15447): GLib-GIO-CRITICAL **: g_dbus_connection_register_object: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed
** (<unknown>:15447): DEBUG: IndicatorAdded: libapplication.so
** (<unknown>:15447): DEBUG: IndicatorAdded: libsoundmenu.so
** (<unknown>:15447): DEBUG: IndicatorAdded: libmessaging.so
** (<unknown>:15447): DEBUG: IndicatorAdded: libdatetime.so
** (<unknown>:15447): DEBUG: IndicatorAdded: libme.so
** (<unknown>:15447): DEBUG: IndicatorAdded: libsession.so
** (<unknown>:15447): DEBUG: IndicatorAdded: libapplication.so
** (<unknown>:15447): DEBUG: IndicatorAdded: libsoundmenu.so
** (<unknown>:15447): DEBUG: IndicatorAdded: libmessaging.so
** (<unknown>:15447): DEBUG: IndicatorAdded: libdatetime.so
** (<unknown>:15447): DEBUG: IndicatorAdded: libme.so
** (<unknown>:15447): DEBUG: IndicatorAdded: libsession.so
Setting Update "command"
Setting Update "initiate_button"
Setting Update "multioutput_mode"
Setting Update "skydome"
Setting Update "skydome_image"
Setting Update "skydome_animated"
Setting Update "active_opacity"
Setting Update "manual_only"
Setting Update "raise_on_rotate"
Setting Update "zoom"
Setting Update "initiate_button"
Setting Update "reflection"
Setting Update "intensity"
Setting Update "deformation"
Setting Update "panel_opacity"
Setting Update "dash_blur_experimental"
** (<unknown>:15447): DEBUG: MaximizeIfBigEnough: Gnome-control-center window size doesn't fit
** (<unknown>:15447): DEBUG: MaximizeIfBigEnough: Ccsm window size doesn't fit
Setting Update "active_plugins"

(<unknown>:15447): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:15447): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:15447): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:15447): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:15447): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:15447): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:15447): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:15447): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:15447): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:15447): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:15447): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:15447): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:15447): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:15447): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:15447): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:15447): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:15447): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:15447): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:15447): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:15447): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:15447): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:15447): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:15447): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:15447): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:15447): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:15447): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:15447): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:15447): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:15447): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:15447): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:15447): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:15447): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:15447): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:15447): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:15447): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:15447): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:15447): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:15447): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:15447): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:15447): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:15447): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:15447): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:15447): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:15447): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:15447): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:15447): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:15447): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:15447): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:15447): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:15447): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:15447): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:15447): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:15447): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:15447): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:15447): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:15447): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:15447): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:15447): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:15447): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:15447): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:15447): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.28.6/./gobject/gsignal.c:2392: instance `0x94bb518' has no handler with id `147'

(<unknown>:15447): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.28.6/./gobject/gsignal.c:2392: instance `0x94bb518' has no handler with id `148'

(<unknown>:15447): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:15447): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:15447): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:15447): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:15447): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `GType'

(<unknown>:15447): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:15447): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `GType'

(<unknown>:15447): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:15447): GLib-CRITICAL **: g_source_unref: assertion `source != NULL' failed


```The whole thing surely looks like a work in progress, but... well... as long as it works, it's good enough for me.

---

### Post by Krytarik on 2011-05-02
Compiz is indeed meant to run in "Ubuntu Classic" (with effects) as well. I guess the reason why it doesn't are the errors you are getting, or another cause I didn't figure so far, as I noticed the same behaviour in another thread.

Anyway, as a workaround just remove Compiz from the session config of "Ubuntu Classic" and add "compiz --replace" to your "Startup Applications" instead.

And to restore the menus to their apps just purge the package "indicator-appmenu".

---

### Post by azupan on 2011-05-02
The ideal solution: Unity and Classic each start Compiz with its own settings. This, I think, would make peaceful coexistence between the three possible.

So far, I came across the following differences

[LIST]
[*]Obviously, Unity plugin must be enabled for unity session, and disabled for Classic session.
[*]General Options, Desktop size. This one was pretty confusing before I figured it out. By default, it's 2x2, and that translates to 2 compiz cubes with 2 workspaces each. Actually, it's compiz plates, unless you have dual monitor. The most sensible configuration for compiz cube under unity is horizontal 4, and vertical 3 (best fit on screen in Expo plugin). IMHO, the ideal configuration is compiz sphere, transparent 3D windows (which makes finding stuff very easy), and desktop size horizontal 3, and vertical 2-3. That translates to 2 separate compiz spheres with 3 workspaces each. Multiple line Expo plugin doesn't work with Classic, so the desktop size setting must be horizontal 4, vertical 1.
[/LIST]
I was gogling around for a suitable Compiz command line argument, but unfortunately, I wasn't able to find anything. 2 different profiles, one for classic, and one for unity seems to be the next best solution. I have yet to try it.

---

### Post by Krytarik on 2011-05-02
> **azupan said:**
> The ideal solution: Unity and Classic each start Compiz with its own settings. This, I think, would make peaceful coexistence between the three possible.

I was gogling around for a suitable Compiz command line argument, but unfortunately, I wasn't able to find anything. 2 different profiles, one for classic, and one for unity seems to be the next best solution. I have yet to try it.
Actually, it *does*, by default. When you open CCSM, click at the lower left at "Preferences", then the option "Profile" should be set to "Default" in "Ubuntu Classic", and to "Unity" in "Ubuntu" (thus Unity), you can also create additional profiles.

The problem is, some users are mixing the settings by modifying them for Unity while they are in Classic, or vice versa.

---

### Post by calande on 2011-05-02
I have a similar problem, OpenGL stopped working with the upgrade to Natty... The best I can get is a window without a title bar :( any idea?

---

### Post by Mad-Halfling on 2011-05-02
I found that enabling the compiz cube, and other settings hosed my window manager when using 11.04 in classic mode, so I went back to Unity.  However there are ways you can get the cube working in Unity, so these should work in classic, too, I would guess.  What I've found is DON'T use the compiz settings manager, this seems to wreak merry hell, but you could try manually editing the config files - this certainly (as I mentioned) worked for the desktop cube in Unity.

Have a look at this

[http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty/](http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty/)

it's supposed to be for Unity but I don't see any reason why it shouldn't work in classic - the downside is that you have to manually edit the config file, but it might help.  Personally I'm really disappointed at this lack of regression functionality from Canonical - I really expected it to be a flawless transition back.  I would imagine this may drive a lot of people away from Ubuntu if they don't want to use Unity and certainly (IMHO) goes against the "Linux for human beings" ethos - I've used Ubuntu for nearly 6 years now, and haven't ever seriously considered changing distro but I actually had Mint downloading in the background while I was poking around with this, in case a reinstall to a different distro was less painful that fixing the problem

---

### Post by azupan on 2011-05-02
> **Krytarik said:**
> Actually, it *does*, by default. When you open CCSM, click at the lower left at "Preferences", then the option "Profile" should be set to "Default" in "Ubuntu Classic", and to "Unity" in "Ubuntu" (thus Unity), you can also create additional profiles.This is exactly what I had in mind. If I could get this into a startup application for Classic somehow... That would solve the problem, I guess.

---

### Post by Krytarik on 2011-05-02
> **calande said:**
> I have a similar problem, OpenGL stopped working with the upgrade to Natty... The best I can get is a window without a title bar :( any idea?
How do you know then that OpenGL isn't working?

Are you indeed using "Ubuntu Classic", too?

Make sure that "Window Decoration" is enabled in "CompizConfig Settings Manager".

Also make sure that the package "compiz" is installed.

If you indeed want to use the "Desktop Cube" instead of the "Desktop Wall", like *Mad-Halfling* presumed, you can also try the method under the title "Update: An alternative gui way" in the guide *Mad-Halfling* posted the link of, it is far easier and should also work, I can't test it because I'm not running a Natty install, but I took a note that it comes to a temporary weird effect upon doing that. But you should relogin anyway after doing that.

Another method I described earlier here:
[http://ubuntuforums.org/showthread.php?p=10748987#post10748987](http://ubuntuforums.org/showthread.php?p=10748987#post10748987)

---

### Post by Krytarik on 2011-05-02
> **azupan said:**
> This is exactly what I had in mind. If I could get this into a startup application for Classic somehow... That would solve the problem, I guess.
You can set/modify the profiles in CCSM, and they should get pulled depending on the session option you choose. At least as far as I understood it. Isn't that the case?

---

### Post by azupan on 2011-05-02
> **calande said:**
> I have a similar problem, OpenGL stopped working with the upgrade to Natty... The best I can get is a window without a title bar :( any idea?

In Ubuntu Unity mode, the following **must** be set in CompizConfig Settings Manager:

[LIST]
[*]Ubuntu Unity Plugin
[*]Expo
[*]Desktop Cube or Desktop Wall
[*]Window Decoration (uncheck this, and window title bars vanish)
[/LIST]
In Classic mode, Ubuntu Unity plugin **may not **be set. Compiz must be run manually.

If you fiddle with the CCSM settings, one or more of the above settings can be unset for a moment, and things go haywire.

If you have troubles even after you set everything right in CCSM, try this:

[LIST]
[*]Reload WM from Compiz Fusion Icon
[*]Logoff/Logon
[*]The following terminal command: ```
gconftool --recursive-unset /apps/compiz-1
```
[/LIST]
If you enable Unity MT Grab Handles & set Toogle Handles to Control-Alt, for example, you can live without window titles & frames as well (you can disable Window Decoration, that is). Looks like Unity guys are planning to get rid of them. A nice idea, if you ask me.

---

### Post by Krytarik on 2011-05-02
> **azupan said:**
> Compiz must be run manually.
I disagree with that to some extent, to a virtually 50/50 one like it seems now. :P
> **azupan said:**
> you can live without window titles & frames as well (you can disable Window Decoration, that is). Looks like Unity guys are planning to get rid of them. A nice idea, if you ask me.
:popcorn::D  Can I keep some please?

To the tune of the currently ubiquitous language, "I HATE titlebar-less unmaximized windows, *at least*!".
And if you don't have any panels at all into which you can integrate the buttons of maximized windows, you will want title bars on those as well. ;-)

---

### Post by azupan on 2011-05-03
> **Krytarik said:**
> I disagree with that to some extent, to a virtually 50/50 one like it seems now. :PWhen and if I manage to figure out how to select from which file or profile to initialize Compiz upon startup, it'll be automatic. Until then, it's manual.
 
> **Krytarik said:**
> 
 
:popcorn::D Can I keep some please?
 
To the tune of the currently ubiquitous language, "I HATE titlebar-less unmaximized windows, *at least*!".
And if you don't have any panels at all into which you can integrate the buttons of maximized windows, you will want title bars on those as well. ;-)Personally, I don't want to keep none of that. Just window contents, and nothing else. Stuff I'm working on, full screen, without any clutter, no frame, to titlebar, nothing. Unity MT Grab Handles mapped to a near-at-finger mouse button would make that possible, if I could get rid of that ](*,)top panel somehow.
 
Right now, I'm using classic Gnome with all the panels hidden, and logitech's side button (the one that comes under the thumb) mapped to Compiz Sphere. When I push it, all my windows pop up in 3d, so I can find them in no time. Who needs friggin window frames & decorations?

---

### Post by Mad-Halfling on 2011-05-03
Just a note regarding the above few posts - I've found (through much playing/testing/cursing) that in classic with the Unity compiz plugin disabled if you do certain things it will screw your desktop every time - one being enabling the cube.  I tried enabling the window decorations but all this did was give me a title bar on *some* windows but these are totally non-functional - you can't move the windows, resize them, etc.  Whatever Canonical has done to the compiz plugins it seems to nerfed them badly - making the equivalent changes, manually, in the config files seems to work ok, so I'd suggest trying that for the moment.  I'm really disappointed with Canonical as this doesn't seem to have been QAed very well, at all.

---

### Post by azupan on 2011-05-03
:rolleyes:> **Mad-Halfling said:**
> Just a note regarding the above few posts - I've found (through much playing/testing/cursing) that in classic with the Unity compiz plugin disabled if you do certain things it will screw your desktop every time - one being enabling the cube.  I tried enabling the window decorations but all this did was give me a title bar on *some* windows but these are totally non-functional - you can't move the windows, resize them, etc.  Whatever Canonical has done to the compiz plugins it seems to nerfed them badly - making the equivalent changes, manually, in the config files seems to work ok, so I'd suggest trying that for the moment.  I'm really disappointed with Canonical as this doesn't seem to have been QAed very well, at all.Now, let's see...

In the ancient times, decades ago, there were xwindows.

On top of xwindows came Gnome & KDE, the archrivals.

On top of Gnome&KDE came Compiz, probably meant as a pure eye candy, but in time, many people found it rather useful, myself included.

On top of Compiz came Unity, as a humble plugin, one of many. However, Unity is supposed to replace Gnome & KDE, upon which Compiz grew up. So... I'm afraid it's not just a bad QA, but a deeper philosophical problem.

Nevertheless, I'm playing, tinkering, and cursing further. So far I was able to figure out there are two profiles in CCSM: Default and Unity. Default is somehow activated in classic mode, Unity in unity mode.

As far as I was able to figure out, the problem that bothers us seems to be caused by automatic plugin activation: You activate Cube Reflection & Deformation, that Enables Cube and disables Wall, that enables OpenGL, OpenGL enables Composite- or at least it's supposed to. In the process, seemingly something crashes, and the whole thing ends up in some weird state. I think the problem can be solved, one way or another, however.

**EDIT:** Got it! When you click "Desktop Cube" for the 1st time in CCSM, all options are cleared for the moment. Because everything takes immediate effects, things go haywire. What a stupid bug!

Workaround: Change Cube/Wall/Expo option only when compiz is not running.

Will fiddle with profiles when time allows.

---

### Post by azupan on 2011-05-03
[LIST=1]
[*]Login as Classic Ubuntu, start CompizConfig Settings Manager, and enable Compiz Cube, or Desktop Wall, whatever you intend to use. Ubuntu Unity Plugin must be disabled.
[*]In terminal window, run ```
exec compiz --replace ccp
``` and Compiz should work. This can be later added to startup programs, or something.
[*]Logout and login as Ubuntu. Now, things get tricky. When you click on Compiz Cube or Compiz Wall, all settings get trashed. You have to prepare your way out of the session in advance. Mine was Logoff button in Cairo Dock, and Ctrl-F1. Saving settings might be a good idea, but Preferences/Profile/Reset to default usually helps.
[*]In CCSM, set everything that has to be set.  Ubuntu Unity plugin must be enabled, of course. Try to ignore any funny stuff happening with the desktop.
[*]Logoff and Logon. At this point, Compiz should work on Unity as well.
[/LIST]
After this, Compiz Cube and Destop Wall plugins may no longer be enabled or disabled, as well as Ubuntu Unity plugin.

Exporting Default and Unity settings might be a good idea.

---

### Post by phalantice on 2011-07-22
In my case i have dual displays in single display mode or if I turn opengl off in copiz it works normally.  for me unity works but I hate it about as much as i do MS...  with dual screens it shifts to the right screen.

---

### Post by azupan on 2011-07-28
Whatever... I gave up on Unity and switched to Kubuntu months ago. Vry nice to work with, and enough of an eye candy to sweeten occassional crashes. I still have an empty partition, will install SUSE & KDE there one of theese days, to see if it works any better.

---

### Post by JoshuaOrtega on 2011-10-15
for some reason I do not have the option to switch to "ubuntu classic session" at start-up..... any reason why? please help. I miss the classic session. I am running 11.04. thank for all the help in the past as well as future help.

---

### Post by Krytarik on 2011-10-15
> **JoshuaOrtega said:**
> for some reason I do not have the option to switch to "ubuntu classic session" at start-up..... any reason why?
Remember that you need to select your username first, so that those options become available, at the bottom panel. If you have passwordless login enabled, you need to disable it before; otherwise, you'd be logged in immediately after selecting your username, obviously.

---

