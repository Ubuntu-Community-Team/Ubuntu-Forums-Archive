---
title: "Desktop Environment Stopped Loading After Trying Xinerama"
date: 2011-10-01
forum: Desktop Environments
---

### Post by gsfgf on 2011-10-01
Hi all, 

I'm newly back to linux in general, and brand new to the ubuntu world, but I figured I'd give y'all a try.  

Anyway, I installed everything with the graphical installer, and it worked fine upon boot, except that my second display wasn't detected.  So I go enable the proprietary nvidia drivers, and use the nvidia utility to configure the display.  At the moment I have the two displays set up as display one rightof zero.  I rebooted the xserver, and my desktop wallpaper did show up on the second display.  I could move my mouse over there, but I couldn't get a desktop icon that I made or a window to actually go onto the second monitor.  

So I decide to try Xinerama and see if that works.  I enable it, restart the xserver, and I get a black screen w/mouse pointer on screen 0 and the desktop wallpaper, but nothing else, on screen 1.  I end up rebooting into console mode so I can actually tinker.  

If I disable Xinerama, I get wallpaper on both displays, a rt. click menu on both displays, and my desktop icon shows up on screen 0 as expected.  However, I get no launcher, menubars, filesystem desktop icons, etc.  I just noticed that the mouse pointer turns into the old X when I move it to screen 1.  

If I re-enable Xinerama, screen 0 is a black screen with mouse pointer.  Screen 1 shows wallpaper and my desktop icon.  Once again, no launcher, etc.  The strange thing is that the mouse input is on the wrong screen.  If I click on scree 1, I get no response.  If I click on screen 0, it sends the signal to what displays on screen 1.  I can rt click on screen 0 and it'll open the rt. click menu on screen 1; I can even hunt around and open my home folder from the desktop icon.  

dmesg doesn't show anything out of the ordinary.  

I do have a big .xsession-errors file.  
```

Xsession: X session started for gsfgf at Sat Oct  1 22:02:31 EDT 2011
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-t8OEMg
SSH_AUTH_SOCK=/tmp/keyring-t8OEMg/ssh
GNOME_KEYRING_PID=4055
GNOME_KEYRING_CONTROL=/tmp/keyring-t8OEMg
SSH_AUTH_SOCK=/tmp/keyring-t8OEMg/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-t8OEMg
SSH_AUTH_SOCK=/tmp/keyring-t8OEMg/ssh
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
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing vpswitch options...done

** (bluetooth-applet:4088): WARNING **: Could not open RFKILL control device, please verify your installation
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
Initializing scale options...done
I/O warning : failed to load external entity "/home/gsfgf/.compiz/session/1031a37bb04ccf27113175209526908600000040390030"
Initializing session options...done
Initializing nautilus-gdu extension

(nautilus:4080): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Starting unity-window-decorator
** (nm-applet:4096): DEBUG: old state indicates that this was not a disconnect 0
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

** (nautilus:4080): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:4080): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:4080): WARNING **: Can not get _NET_WORKAREA

** (nautilus:4080): WARNING **: Can not determine workarea, guessing at layout
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing staticswitcher options...done
Initializing resize options...done
Initializing fade options...done
Initializing scale options...done
I/O warning : failed to load external entity "/home/gsfgf/.compiz/session/1031a37bb04ccf27113175209526908600000040390030"
Initializing session options...done
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:4080): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4080): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4080): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4080): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4080): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4080): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4080): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4080): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4080): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4080): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4080): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4080): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
Setting Update "run_command_terminal_key"
Setting Update "fullscreen_visual_bell"
x-session-manager: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0" 
gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
      after 2719 requests (2719 known processed) with 6 events remaining. 
unity-window-decorator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
Xsession: X session started for gsfgf at Sat Oct  1 22:07:08 EDT 2011
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-OgwzEH
SSH_AUTH_SOCK=/tmp/keyring-OgwzEH/ssh
GNOME_KEYRING_PID=4260
GNOME_KEYRING_CONTROL=/tmp/keyring-OgwzEH
SSH_AUTH_SOCK=/tmp/keyring-OgwzEH/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-OgwzEH
SSH_AUTH_SOCK=/tmp/keyring-OgwzEH/ssh
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
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done

** (bluetooth-applet:4293): WARNING **: Could not open RFKILL control device, please verify your installation
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
Initializing nautilus-gdu extension
Initializing scale options...done
I/O warning : failed to load external entity "/home/gsfgf/.compiz/session/109f2af582983b6c7d131752122848017500000042440030"
Initializing session options...done

(nautilus:4284): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Starting unity-window-decorator

(unity-window-decorator:4350): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(unity-window-decorator:4350): Gdk-CRITICAL **: IA__gdk_window_set_events: assertion `GDK_IS_WINDOW (window)' failed

(unity-window-decorator:4350): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(unity-window-decorator:4350): Gdk-CRITICAL **: IA__gdk_window_set_events: assertion `GDK_IS_WINDOW (window)' failed

(unity-window-decorator:4350): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(unity-window-decorator:4350): Gdk-CRITICAL **: IA__gdk_window_set_events: assertion `GDK_IS_WINDOW (window)' failed

(unity-window-decorator:4350): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(unity-window-decorator:4350): Gdk-CRITICAL **: IA__gdk_window_set_events: assertion `GDK_IS_WINDOW (window)' failed

(unity-window-decorator:4350): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(unity-window-decorator:4350): Gdk-CRITICAL **: IA__gdk_window_set_events: assertion `GDK_IS_WINDOW (window)' failed

(unity-window-decorator:4350): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(unity-window-decorator:4350): Gdk-CRITICAL **: IA__gdk_window_set_events: assertion `GDK_IS_WINDOW (window)' failed

(unity-window-decorator:4350): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(unity-window-decorator:4350): Gdk-CRITICAL **: IA__gdk_window_set_events: assertion `GDK_IS_WINDOW (window)' failed

(unity-window-decorator:4350): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(unity-window-decorator:4350): Gdk-CRITICAL **: IA__gdk_window_set_events: assertion `GDK_IS_WINDOW (window)' failed
** (nm-applet:4299): DEBUG: old state indicates that this was not a disconnect 0
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

** (nautilus:4284): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:4284): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:4284): WARNING **: Can not get _NET_WORKAREA

** (nautilus:4284): WARNING **: Can not determine workarea, guessing at layout
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing staticswitcher options...done
Initializing resize options...done
Initializing fade options...done
Initializing scale options...done
I/O warning : failed to load external entity "/home/gsfgf/.compiz/session/109f2af582983b6c7d131752122848017500000042440030"
Initializing session options...done
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
Setting Update "run_command_terminal_key"
Setting Update "fullscreen_visual_bell"

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:4284): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

```Also, my console (without x) is shifted a few pixels left.  I installed fbcon, but can't get it to move.  I doubt this is related, but who knows.  Also, it would be nice to adjust that so I can see the left edge of config files while I'm troubleshooting.  

Y'all got any ideas?  

(Btw, I changed my userid and then chown -R gsfgf /home/gsfgf, but it loaded X the one time I tried before monkeying with the x server settings, so that shouldn't be it.  Just being thorough)

---

### Post by sumski on 2011-10-03
This is *probably* happening 'cause you can't use xinerama + compositing. Try twinview

---

### Post by Andrea9 on 2011-10-14
I've the same problem.

TwinView working properly but the problem is windows full screen. In TwinView occupies only one monitor instead of 2.

Xinerama and Unity 2d working good..


PS Sorry for my english

---

