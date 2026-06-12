---
title: "Can't launch succesfully compiled Gnome Shell"
date: 2011-07-01
forum: Desktop Environments
---

### Post by tigull on 2011-07-01
After many failures, I succesfully compiled Gnome Shell from GIT. I already did about two months ago on the same machine and everything went ace. This time, when trying to finally launch it with ./gnome-shell --replace, the windows briefly disappear, the screen flashes for a few seconds but the Unity or the Classic Ubuntu desktop are restored normally. This is the output in the terminal:
 
 
```
giulio@giulio-902:~$ ~/gnome-shell/source/gnome-shell/src/gnome-shell --replace
Gtk-Message: Failed to load module "canberra-gtk-module"
Window manager warning: Log level 8: gtk_style_context_add_provider: assertion `GTK_IS_STYLE_PROVIDER (provider)' failed
    JS ERROR: !!!   Exception was: Error: Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = '"gjs_throw"'
    JS ERROR: !!!     stack = '"("Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found")@gjs_throw:0
@/home/giulio/gnome-shell/source/gnome-shell/js/ui/status/network.js:8
"'
    JS ERROR: !!!     message = '"Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found"'
GLib-GIO-ERROR **: Settings schema 'org.gnome.nautilus.desktop' is not installed
gnome-shell-calendar-server[8421]: Got HUP on stdin - exiting
Shell killed with signal 5
giulio@giulio-902:~$ Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
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
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
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
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing snap options...done
Initializing move options...done
Initializing unitymtgrabhandles options...done
Initializing vpswitch options...done
Initializing grid options...done
Initializing mousepoll options...done
Initializing obs options...done
Initializing resize options...done
Initializing gnomecompat options...done
Initializing animation options...done
Initializing commands options...done
Initializing workarounds options...done
Initializing place options...done
Initializing session options...done
Initializing kdecompat options...done
Initializing expo options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing staticswitcher options...done
Initializing fade options...done
Initializing scale options...done
** (<unknown>:8426): DEBUG: Unity accessibility initialization
** (<unknown>:8426): DEBUG: Shows on edge: 1
Screen geometry changed:
  Monitor 0(primary)
   0x0x1366x768
** (<unknown>:8426): DEBUG: PanelController:: Added Panel for Monitor 0
Initializing unityshell options...done
giulio@giulio-902:~$ ** (<unknown>:8426): DEBUG: MaximizeIfBigEnough: Gnome-terminal window size doesn't fit
giulio@giulio-902:~$ ** (<unknown>:8426): DEBUG: PlaceEntry: Applications
** (<unknown>:8426): DEBUG: PlaceEntry: Commands
** (<unknown>:8426): DEBUG: PlaceEntry: Files & Folders
** (<unknown>:8426): DEBUG: /com/canonical/unity/applicationsplace
** (<unknown>:8426): DEBUG: /com/canonical/unity/filesplace
** (<unknown>:8426): DEBUG: Setting to primary screen rect: x=0 y=0 w=1366 h=768
** (<unknown>:8426): DEBUG: Acquired the name com.canonical.Unity.Launcher on the session bus
 
** (<unknown>:8426): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window56623581: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist
 
** (<unknown>:8426): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window56623581: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist
giulio@giulio-902:~$ ** (<unknown>:8426): DEBUG: IndicatorAdded: libapplication.so
** (<unknown>:8426): DEBUG: IndicatorAdded: libsoundmenu.so
** (<unknown>:8426): DEBUG: IndicatorAdded: libmessaging.so
** (<unknown>:8426): DEBUG: IndicatorAdded: libdatetime.so
** (<unknown>:8426): DEBUG: IndicatorAdded: libme.so
** (<unknown>:8426): DEBUG: IndicatorAdded: libsession.so
Setting Update "sync_to_vblank"
Setting Update "top_left_corner_action"
Setting Update "top_right_corner_action"
Setting Update "bottom_left_corner_action"
Setting Update "bottom_right_corner_action"
Setting Update "indicator_direction"
Setting Update "run_command_terminal_key"
Setting Update "command0"
Setting Update "command1"
Setting Update "run_command0_key"
Setting Update "run_command1_key"
Setting Update "fullscreen_visual_bell"
Setting Update "launcher_reveal_edge"
Setting Update "launcher_hide_mode"
Setting Update "backlight_mode"
Setting Update "panel_opacity"
Setting Update "icon_size"
``` 
 
notice that it seems as if Gnome Shell is actually running.
 
If you have ideas on how to fix or work this around, any help is appreciated!

---

### Post by FormatSeize on 2011-07-01
> **tigull said:**
> After many failures, I succesfully compiled Gnome Shell from GIT.
Congratulations. As I'm working on LFS, which is causing me to hate computers in general, this seems like a feat to me. 
 
 
> **tigull said:**
> ```

"'
    JS ERROR: !!!     message = '"Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found"'
GLib-GIO-ERROR **: Settings schema 'org.gnome.nautilus.desktop' is not installed
gnome-shell-calendar-server[8421]: Got HUP on stdin - exiting
Shell killed with signal 5
```
 

Your build is looking for NetworkManager, and not being able to find it is causing it to get killed off. Your host system has it, that's likely why the build went okay, but now it seems to be looking for it within itself, and can't find it. A quick look at what exactly NetworkManager is makes me quite curious as to why something so non-essential would cause the shell initialization to fail. 
Do you recall building that along with everything else? The actual package name is network-manager. 
 
As for the shell running, it seems that the windowing messages you see are actually your host system's shell re-initializing.

---

### Post by tigull on 2011-07-01
> Do you recall building that along with everything else?
 I didn't build anything along with it, and in the module list there is no network-manager package. I just tried building NetworkManager from GIT but I get the following error 

```
configure: error: wireless-tools library and development headers >= 28pre9 not installed or not functional

```


when I actually have version 30pre9. I'll see if I can fix that but I don't really know where to begin.

---

