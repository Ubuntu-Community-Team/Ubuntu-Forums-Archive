---
title: "unity reset trouble"
date: 2012-04-08
forum: Desktop Environments
---

### Post by boregard on 2012-04-08
Hello all, I was trying to get the cube working and got everything messed up. So I am trying to reset Unity. I get these errors when I run the reset command. Any advice on fixing this problem will be appreciated. Thanks~$ unity --reset
WARNING: Unity currently default profile, so switching to metacity while resetting the values

(metacity:2554): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(metacity:2554): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(metacity:2554): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(metacity:2554): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
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
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing snap options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing resize options...done
Initializing fade options...done
Initializing unitymtgrabhandles options...done
Initializing scale options...done
Initializing session options...done

Screen geometry changed:
   0x0x1920x1080

unity-panel-service: no process found
Initializing unityshell options...done
WARN  2012-04-08 00:27:42 unity.favorites FavoriteStoreGSettings.cpp:138 Unable to load GDesktopAppInfo for 'ubiquity-gtkui.desktop'
DEBUG 2012-04-08 00:27:42 glib <unknown>:0 Setting to primary screen rect: x=0 y=0 w=1920 h=1080
WARN  2012-04-08 00:27:42 glib <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/window60817569: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

Initializing addhelper options...done
Initializing animationaddon options...done
Initializing annotate options...done
Initializing bench options...done
Initializing blur options...done
Initializing clone options...done
Initializing colorfilter options...done
Initializing commands options...done
Initializing crashhandler options...done
Initializing cube options...done
Initializing cubeaddon options...done
Initializing debugspew options...done
Initializing extrawm options...done
Initializing fadedesktop options...done
Initializing firepaint options...done
Initializing group options...done
Initializing imgjpeg options...done
Initializing kdecompat options...done
Initializing loginout options...done
Initializing mag options...done
Initializing maximumize options...done
Initializing mblur options...done
Initializing neg options...done
Initializing notification options...done
Initializing obs options...done
Initializing opacify options...done
Initializing put options...done
Initializing reflex options...done
Initializing resizeinfo options...done
Initializing ring options...done
Initializing rotate options...done
Initializing scaleaddon options...done
Initializing scalefilter options...done
Initializing screenshot options...done
Initializing shelf options...done
Initializing shift options...done
Initializing showdesktop options...done
Initializing showmouse options...done
Initializing splash options...done
Initializing staticswitcher options...done
Initializing switcher options...done
Initializing td options...done
Initializing thumbnail options...done
Initializing trailfocus options...done
Initializing wallpaper options...done
Initializing water options...done
Initializing widget options...done
Initializing winrules options...done
Initializing wobbly options...done
Initializing zoom options...done
Setting Update "main_menu_key"
Setting Update "run_key"
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x34000e9

---

### Post by dylan07 on 2012-04-08
Can you go into ccsm and set the settings you changed to default? And can you remember any warning messages, about anything being disabled?

---

### Post by boregard on 2012-04-08
> **dylan07 said:**
> Can you go into ccsm and set the settings you changed to default? And can you remember any warning messages, about anything being disabled?
Went into ccsm and it looks like everything is set to default. Thanks

---

### Post by boregard on 2012-04-08
Hi all, I got cube working correctly by following directions from this link [URL="http://ubuntuforums.org/Setting%20up%20the%20Cube%20and%20Desktop%20Effects%20in%20Compiz"]https://help.ubuntu.com/community/CompositeManager
[/URL]

---

