---
title: "How to debug long log-in?"
date: 2013-11-23
forum: Desktop Environments
---

### Post by mindbox on 2013-11-23
Hello, 

I've found the following problems with my lightdm greeter.log. Could anyone help me understand how to troubleshoot the problem. I've looked online and have found many people with different solutions. How do I learn what is causing these WARNING's so I can fix them myself in the future? I would like my computer to boot-up and log-in faster. The login takes over a minute sometimes. 

I'm running 12.04 LTS with cinnamon, ubuntu, gnome, kde, and some others. I'm using lightdm, but when i switch to gdm I have the same problems. 

Thank You

[HTML][+0.00s] DEBUG: unity-greeter.vala:895: Starting unity-greeter 0.2.9 UID=115 LANG=en_US.UTF-8
[+0.00s] DEBUG: unity-greeter.vala:898: Setting cursor
Activating service name='org.a11y.atspi.Registry'
Successfully activated service 'org.a11y.atspi.Registry'

** (at-spi2-registryd:2729): WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

** (at-spi2-registryd:2729): WARNING **: Unable to register client with session manager
[+0.95s] DEBUG: unity-greeter.vala:902: Creating background surface
[+0.95s] DEBUG: unity-greeter.vala:905: Loading command line options
[+0.95s] DEBUG: unity-greeter.vala:933: Setting GTK+ settings
[+3.96s] WARNING: Theme parsing error: gtk-widgets-assets.css:443:52: Error opening file: No such file or directory
[+3.96s] WARNING: Theme parsing error: gtk-widgets-assets.css:447:61: Error opening file: No such file or directory
[+3.96s] WARNING: Theme parsing error: gtk-widgets-assets.css:451:60: Error opening file: No such file or directory
[+3.96s] WARNING: Theme parsing error: gtk-widgets-assets.css:455:61: Error opening file: No such file or directory
[+3.96s] WARNING: Theme parsing error: gtk-widgets-assets.css:459:70: Error opening file: No such file or directory
[+3.96s] WARNING: Theme parsing error: gtk-widgets-assets.css:463:68: Error opening file: No such file or directory
[+3.99s] WARNING: Theme parsing error: gtk-widgets.css:305:22: Not a valid image
[+3.99s] WARNING: Theme parsing error: gtk-widgets.css:309:22: Not a valid image
[+3.99s] WARNING: Theme parsing error: gtk-widgets.css:1136:23: Horizontal and vertical offsets are required
[+3.99s] WARNING: Theme parsing error: gtk-widgets.css:1142:24: 'px' is not a valid color name
[+3.99s] WARNING: Theme parsing error: gtk-widgets.css:1235:24: 'px' is not a valid color name
[+4.32s] WARNING: Theme parsing error: gtk-widgets.css:1926:11: Not using units is deprecated. Assuming 'px'.
[+4.32s] WARNING: Theme parsing error: gtk-widgets.css:1998:14: Not using units is deprecated. Assuming 'px'.
[+4.38s] WARNING: Theme parsing error: gtk-widgets-backdrop.css:131:4: not a number
[+4.38s] WARNING: Theme parsing error: gtk-widgets-backdrop.css:152:4: not a number
[+4.38s] WARNING: Theme parsing error: gtk-widgets-backdrop.css:171:4: not a number
[+4.51s] DEBUG: unity-greeter.vala:956: Creating Unity Greeter
[+4.51s] DEBUG: Connecting to display manager...
[+4.51s] DEBUG: Wrote 17 bytes to daemon
[+4.52s] DEBUG: Read 8 bytes from daemon
[+4.52s] DEBUG: Read 120 bytes from daemon
[+4.52s] DEBUG: Connected version=1.2.3 default-session=ubuntu show-manual-login=false hide-users=false has-guest-account=true
[+5.53s] DEBUG: menubar.vala:359: LANG=en_US.UTF-8 LANGUAGE=(null)
[+12.88s] CRITICAL: g_error_free: assertion `error != NULL' failed
[+12.90s] DEBUG: get entries
[+12.90s] DEBUG: menubar.vala:541: Adding indicator object 0x2773078 at position 0
[+13.02s] DEBUG: Evaluating bitmask for '%l:%M %p'
[+13.02s] DEBUG: Checking against 2 possible times
[+13.75s] DEBUG: Guessing max time width: 62
[+13.92s] DEBUG: get entries
[+13.92s] DEBUG: menubar.vala:541: Adding indicator object 0x2a57188 at position 1
[+13.94s] WARNING: IndicatorObject class does not have an accessible description.
[+14.23s] WARNING: Unable to load icon from file 'audio-output-none' because: Failed to open file 'audio-output-none': No such file or directory
[+14.24s] WARNING: IndicatorObject class does not have an accessible description.
[+14.24s] DEBUG: get entries
[+14.24s] DEBUG: get entries
[+14.24s] DEBUG: menubar.vala:541: Adding indicator object 0x2aad0d8 at position 2
[+14.29s] DEBUG: menubar.vala:365: LANG=en_US.UTF-8 LANGUAGE=(null)
[+14.37s] DEBUG: Loaded session /usr/share/xsessions/xterm.desktop (Recovery Console, Failsafe session with only xterm)
[+14.39s] DEBUG: Loaded session /usr/share/xsessions/ubuntu-2d.desktop (Ubuntu 2D, This session logs you into Ubuntu 2D Mode)
[+14.42s] DEBUG: Loaded session /usr/share/xsessions/enlightenment.desktop (Enlightenment, Log in using Enlightenment (Version 0.16.999.55225))
[+14.45s] DEBUG: Loaded session /usr/share/xsessions/LXDE.desktop (LXDE, LXDE - Lightweight X11 desktop environment)
[+14.47s] DEBUG: Loaded session /usr/share/xsessions/cinnamon2d.desktop (Cinnamon (Software Rendering), This session logs you into Cinnamon (using software rendering))
[+14.49s] DEBUG: Loaded session /usr/share/xsessions/cairo-dock-fallback.desktop (Cairo-Dock (Gnome No effects), This session logs you into GNOME with Cairo-Dock and without any graphical effect.)
[+14.51s] DEBUG: Loaded session /usr/share/xsessions/cairo-dock.desktop (Cairo-Dock (Gnome + Effects), This session logs you into GNOME with Cairo-Dock and with graphical effects.)
[+14.54s] DEBUG: Loaded session /usr/share/xsessions/xfce.desktop (Xfce Session, Use this session to run Xfce as your desktop environment)
[+14.55s] DEBUG: Loaded session /usr/share/xsessions/awesome.desktop (awesome, Highly configurable framework window manager)
[+14.57s] DEBUG: Loaded session /usr/share/xsessions/cairo-dock-unity.desktop (Cairo-Dock (with Unity Panel), This session logs you into GNOME with Cairo-Dock and Unity-2D panel)
[+14.58s] DEBUG: Loaded session /usr/share/xsessions/xmonad.desktop (XMonad, Lightweight tiling window manager)
[+14.63s] DEBUG: Loaded session /usr/share/xsessions/IceWM.desktop (IceWM, This is the window manager IceWM)
[+14.65s] DEBUG: Loaded session /usr/share/xsessions/gnome.desktop (GNOME, This session logs you into GNOME)
[+14.66s] DEBUG: Loaded session /usr/share/xsessions/cinnamon.desktop (Cinnamon, This session logs you into Cinnamon)
[+14.68s] DEBUG: Loaded session /usr/share/xsessions/icewm-session.desktop (icewm, Simple and fast window manger)
[+14.69s] DEBUG: Loaded session /usr/share/xsessions/fluxbox.desktop (Fluxbox, Highly configurable and low resource X11 Window manager)
[+14.70s] DEBUG: Loaded session /usr/share/xsessions/gnome-xmonad.desktop (GNOME with Xmonad, A GNOME fallback mode session using xmonad as the window manager.)
[+14.71s] DEBUG: Loaded session /usr/share/xsessions/openbox-gnome.desktop (GNOME/Openbox, Use the Openbox window manager inside of the GNOME desktop environment)
[+14.72s] DEBUG: Loaded session /usr/share/xsessions/kde-plasma.desktop (KDE Plasma Workspace, The desktop made by KDE)
[+14.74s] DEBUG: Loaded session /usr/share/xsessions/gnome-classic.desktop (GNOME Classic, This session logs you into GNOME with the traditional panel)
[+14.75s] DEBUG: Loaded session /usr/share/xsessions/wmii.desktop (Wmii, Window manager improved 3)
[+14.77s] DEBUG: Loaded session /usr/share/xsessions/XBMC.desktop (XBMC, This session will start XBMC Media Center)
[+14.77s] DEBUG: Loaded session /usr/share/xsessions/openbox-kde.desktop (KDE/Openbox, Use the Openbox window manager inside of the K Desktop Environment)
[+14.77s] DEBUG: Loaded session /usr/share/xsessions/ubuntu.desktop (Ubuntu, This session logs you into Ubuntu)
[+14.77s] DEBUG: Loaded session /usr/share/xsessions/gnome-fallback.desktop (GNOME Classic (No effects), This session logs you into GNOME with the traditional panel without any graphical effect.)
[+14.78s] DEBUG: Loaded session /usr/share/xsessions/openbox.desktop (Openbox, Log in using the Openbox window manager (without a session manager))
[+14.78s] DEBUG: session-chooser.vala:42: Adding session cairo-dock (Cairo-Dock (Gnome + Effects))
[+14.78s] DEBUG: session-chooser.vala:42: Adding session cairo-dock-fallback (Cairo-Dock (Gnome No effects))
[+14.78s] DEBUG: session-chooser.vala:42: Adding session cairo-dock-unity (Cairo-Dock (with Unity Panel))
[+14.78s] DEBUG: session-chooser.vala:42: Adding session cinnamon (Cinnamon)
[+14.78s] DEBUG: session-chooser.vala:42: Adding session cinnamon2d (Cinnamon (Software Rendering))
[+14.78s] DEBUG: session-chooser.vala:42: Adding session enlightenment (Enlightenment)
[+14.78s] DEBUG: session-chooser.vala:42: Adding session fluxbox (Fluxbox)
[+14.78s] DEBUG: session-chooser.vala:42: Adding session gnome (GNOME)
[+14.80s] DEBUG: session-chooser.vala:42: Adding session gnome-classic (GNOME Classic)
[+14.83s] DEBUG: session-chooser.vala:42: Adding session gnome-fallback (GNOME Classic (No effects))
[+14.84s] DEBUG: session-chooser.vala:42: Adding session gnome-xmonad (GNOME with Xmonad)
[+14.84s] DEBUG: session-chooser.vala:42: Adding session openbox-gnome (GNOME/Openbox)
[+14.84s] DEBUG: session-chooser.vala:42: Adding session IceWM (IceWM)
[+14.84s] DEBUG: session-chooser.vala:42: Adding session kde-plasma (KDE Plasma Workspace)
[+14.84s] DEBUG: session-chooser.vala:42: Adding session openbox-kde (KDE/Openbox)
[+14.84s] DEBUG: session-chooser.vala:42: Adding session LXDE (LXDE)
[+14.85s] DEBUG: session-chooser.vala:42: Adding session openbox (Openbox)
[+14.85s] DEBUG: session-chooser.vala:42: Adding session xterm (Recovery Console)
[+14.85s] DEBUG: session-chooser.vala:42: Adding session ubuntu (Ubuntu)
[+14.86s] DEBUG: session-chooser.vala:42: Adding session ubuntu-2d (Ubuntu 2D)
[+14.86s] DEBUG: session-chooser.vala:42: Adding session wmii (Wmii)
[+14.86s] DEBUG: session-chooser.vala:42: Adding session XBMC (XBMC)
[+14.86s] DEBUG: session-chooser.vala:42: Adding session xmonad (XMonad)
[+14.86s] DEBUG: session-chooser.vala:42: Adding session xfce (Xfce Session)
[+14.86s] DEBUG: session-chooser.vala:42: Adding session awesome (awesome)
[+14.86s] DEBUG: session-chooser.vala:42: Adding session icewm-session (icewm)
[+15.13s] DEBUG: Setting keyboard layout to 'us'
[+15.29s] DEBUG: main-window.vala:98: Screen is 1600x900 pixels
[+15.29s] DEBUG: main-window.vala:104: Monitor 0 is 1600x900 pixels at 0,0
[+15.29s] DEBUG: Loading users from org.freedesktop.Accounts
[+15.29s] DEBUG: Loading user /org/freedesktop/Accounts/User1001
[+15.36s] DEBUG: Loading user /org/freedesktop/Accounts/User1000
[+15.37s] DEBUG: Loading sessions from org.freedesktop.DisplayManager
[+15.37s] DEBUG: unity-greeter.vala:332: Adding/updating user guest (Guest)
[+15.37s] DEBUG: unity-greeter.vala:332: Adding/updating user dan (dan)
[+15.37s] DEBUG: unity-greeter.vala:189: Adding guest account entry
[+15.44s] DEBUG: Starting authentication for user dan...
[+15.44s] DEBUG: Wrote 19 bytes to daemon
[+15.44s] DEBUG: unity-greeter.vala:959: Showing greeter
[+15.44s] DEBUG: unity-greeter.vala:357: Showing main window
[+15.44s] DEBUG: New style for time label
[+15.44s] DEBUG: Evaluating bitmask for '%l:%M %p'
[+15.44s] DEBUG: Checking against 2 possible times
[+15.44s] DEBUG: Guessing max time width: 62
[+15.44s] WARNING: Unable to load icon from file 'audio-output-none' because: Failed to open file 'audio-output-none': No such file or directory
[+15.51s] DEBUG: background.vala:315: Regenerating backgrounds
[+15.51s] DEBUG: background.vala:67: Making background /usr/share/backgrounds/edubuntu_default.png at 1600x900
[+15.51s] DEBUG: New style for time label
[+15.51s] DEBUG: Evaluating bitmask for '%l:%M %p'
[+15.51s] DEBUG: Checking against 2 possible times
[+15.51s] DEBUG: Guessing max time width: 62
[+15.55s] DEBUG: unity-greeter.vala:972: Starting main loop
[+15.55s] DEBUG: Read 8 bytes from daemon
[+15.55s] DEBUG: Read 33 bytes from daemon
[+15.55s] DEBUG: Prompt user with 1 message(s)
[+16.21s] CRITICAL: gtk_widget_event: assertion `WIDGET_REALIZED_FOR_EVENT (widget, event)' failed
[+16.24s] DEBUG: background.vala:67: Making background /usr/share/backgrounds/Twilight_Frost_by_Phil_Jackson.jpg at 1600x900
[+16.24s] DEBUG: Setting keyboard layout to 'us'
[+16.30s] DEBUG: Num devices: '2'

[+16.30s] DEBUG: get_primary_device: got data from object /org/freedesktop/UPower/devices/line_power_ACAD
[+16.30s] DEBUG: get_primary_device: got data from object /org/freedesktop/UPower/devices/battery_BAT1
[+16.30s] DEBUG: put_primary_device: got data from object /org/freedesktop/UPower/devices/battery_BAT1
[+16.30s] DEBUG: set_accessible_desc: setting accessible description to 'Battery (2 minutes to charge (56%))'
[+16.30s] DEBUG: Num devices: '2'

[+16.30s] DEBUG: menu_add_device: got data from object /org/freedesktop/UPower/devices/line_power_ACAD
[+16.30s] DEBUG: menu_add_device: got data from object /org/freedesktop/UPower/devices/battery_BAT1
[+16.30s] DEBUG: icon_policy is: 0 (present==0, charge==1, never==2)
[+16.30s] DEBUG: count_batteries found 1 batteries (1 are charging/discharging)
[+16.30s] DEBUG: should_be_visible: yes
[+16.30s] DEBUG: refresh_entry_accessible_desc: setting entry 0x260c638 accessible description to 'Battery (2 minutes to charge (56%))'
[+16.30s] DEBUG: get entries
[+16.30s] DEBUG: get entries
[+16.30s] DEBUG: get entries
[+16.30s] DEBUG: menubar.vala:541: Adding indicator object 0x260c638 at position 2
[+16.42s] DEBUG: Connected to Application Indicator Service.
[+16.43s] DEBUG: unity-greeter.vala:315: starting system-ready sound
[+18.65s] DEBUG: background.vala:116: Render of background /usr/share/backgrounds/edubuntu_default.png complete
[+18.67s] DEBUG: Request current apps
[+18.68s] DEBUG: background.vala:116: Render of background /usr/share/backgrounds/Twilight_Frost_by_Phil_Jackson.jpg complete
[+18.70s] DEBUG: Restarting service 'com.canonical.indicator.session' count 1
[+18.71s] DEBUG: Restarting service 'com.canonical.indicator.datetime' count 1
[+18.71s] DEBUG: indicator-sound: new_volume_slider_widget
[+18.72s] DEBUG: indicator-sound: new_voip_slider_widget
[+18.74s] WARNING: Getting layout failed: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface `com.canonical.dbusmenu' on object at path /com/canonical/indicator/users/menu
[+18.77s] DEBUG: notify visible signal received
[+18.77s] CRITICAL: ido_calendar_menu_item_set_date: assertion `IDO_IS_CALENDAR_MENU_ITEM(menuitem)' failed
[+18.77s] DEBUG: New calendar item
[+29.09s] DEBUG: Providing response to display manager
[+29.09s] DEBUG: Wrote 25 bytes to daemon
[+30.31s] DEBUG: Read 8 bytes from daemon
[+30.31s] DEBUG: Read 15 bytes from daemon
[+30.31s] DEBUG: Authentication complete for user dan with return code 0
[+30.32s] DEBUG: Starting session ubuntu
[+30.32s] DEBUG: Wrote 18 bytes to daemon
[+30.32s] DEBUG: Read 8 bytes from daemon
[+30.32s] DEBUG: Read 4 bytes from daemon

[/HTML]

---

### Post by mindbox on 2013-12-16
I installed ubuntu in virtual box and the lightdm greeter log looked very similar to thise. So my guess is that nothing here indicated the problem with my slow login.

---

