---
title: "indicator-applet missing"
date: 2011-08-29
forum: Desktop Environments
---

### Post by Luke Kijanovich on 2011-08-29
Today when I turned on my PC, indicator plugin on upper panel was gone. I checked out panel settings, but it appears that plugin is still there, i just can't use it or see it. 

I use Xubuntu 11.04.

---

### Post by raja.genupula on 2011-08-30
restart the system and give a look .

---

### Post by Toz on 2011-08-30
You can also try removing and re-adding the plugin. If that still doesn't work, have a look at a hidden file in your home directory called **.xsession-errors** for some hints as to what might be happening. Feel free to post back the contents of that file if you need a second pair of eyes to have a look.

---

### Post by Luke Kijanovich on 2011-08-31
I tried re-adding plugin already, that didn't work. Plugin only flashes for a second and then disappears again. As for .xsession-errors here's part referencing indicator-plugin:
```

(xfce4-indicator-plugin:1732): GLib-CRITICAL **: g_strv_length: assertion `str_array != NULL' failed
(xfce4-indicator-plugin:1732): xfce4-indicator-plugin-DEBUG: Looking at Module: libme.so
(xfce4-indicator-plugin:1732): xfce4-indicator-plugin-DEBUG: Loading Module: libme.so
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/blueman/plugins/AppletPlugin.py", line 105, in _load
    self.on_load(applet)
  File "/usr/lib/python2.7/dist-packages/blueman/plugins/applet/PulseAudio.py", line 115, in on_load
    if int(version.split(".")[2]) < 15:
ValueError: invalid literal for int() with base 10: '22-24-g67d18'
(xfce4-indicator-plugin:1732): xfce4-indicator-plugin-DEBUG: Looking at Module: libsession.so
(xfce4-indicator-plugin:1732): xfce4-indicator-plugin-DEBUG: Loading Module: libsession.so
(xfce4-indicator-plugin:1732): xfce4-indicator-plugin-DEBUG: Looking at Module: libnetworkmenu.so
(xfce4-indicator-plugin:1732): xfce4-indicator-plugin-DEBUG: Loading Module: libnetworkmenu.so
** (xfce4-indicator-plugin:1732): DEBUG: get_menu()

(xfce4-indicator-plugin:1732): libindicator-WARNING **: IndicatorObject class does not have an accessible description.
(xfce4-indicator-plugin:1732): xfce4-indicator-plugin-DEBUG: Looking at Module: libapplication.so
(xfce4-indicator-plugin:1732): xfce4-indicator-plugin-DEBUG: Loading Module: libapplication.so
(xfce4-indicator-plugin:1732): xfce4-indicator-plugin-DEBUG: Looking at Module: libappmenu.so
(xfce4-indicator-plugin:1732): xfce4-indicator-plugin-DEBUG: Loading Module: libappmenu.so

(xfce4-indicator-plugin:1732): Indicator-Appmenu-WARNING **: Unable to find the file menu stock item
(xfce4-indicator-plugin:1732): xfce4-indicator-plugin-DEBUG: Looking at Module: libsoundmenu.so
(xfce4-indicator-plugin:1732): xfce4-indicator-plugin-DEBUG: Loading Module: libsoundmenu.so
GLib-GIO-Message: Using the 'memory' GSettings backend.  Your settings will not be saved or shared with other applications.

(xfce4-indicator-plugin:1732): libindicator-WARNING **: IndicatorObject class does not have an accessible description.
(xfce4-indicator-plugin:1732): xfce4-indicator-plugin-DEBUG: Looking at Module: libmessaging.so
(xfce4-indicator-plugin:1732): xfce4-indicator-plugin-DEBUG: Loading Module: libmessaging.so

(xfce4-indicator-plugin:1732): libindicator-WARNING **: IndicatorObject class does not have an accessible description.

(xfce4-indicator-plugin:1732): libxfce4panel-CRITICAL **: IA__xfce_panel_plugin_add_action_widget: assertion `GTK_IS_WIDGET (widget)' failed
(xfce4-indicator-plugin:1732): Indicator-Appmenu-DEBUG: New Desktop Window: 1800003
(xfce4-indicator-plugin:1732): Indicator-Application-DEBUG: Connected to Application Indicator Service.
** (xfce4-indicator-plugin:1732): DEBUG: new_tech_menuitem()
** (xfce4-indicator-plugin:1732): DEBUG: new_tech_menuitem()
(xfce4-indicator-plugin:1732): Indicator-Application-DEBUG: Request current apps
(xfce4-indicator-plugin:1732): Indicator-Appmenu-DEBUG: Registering window ID 44040196 with path /com/canonical/menu/2A00004 from :1.34
(xfce4-indicator-plugin:1732): Indicator-Appmenu-DEBUG: Creating new windows menu: 2A00004, :1.34, /com/canonical/menu/2A00004
(xfce4-indicator-plugin:1732): Indicator-Appmenu-DEBUG: Active window is: NULL
(xfce4-indicator-plugin:1732): Indicator-Appmenu-DEBUG: Switching to menus from XID 0
(xfce4-indicator-plugin:1732): Indicator-Messages-DEBUG: new_application_item ("Set Up Broadcast Account...")
(xfce4-indicator-plugin:1732): Indicator-Messages-DEBUG: new_application_item ("Ubuntu One")
(xfce4-indicator-plugin:1732): Indicator-Sound-DEBUG: indicator-sound: new_volume_slider_widget
(xfce4-indicator-plugin:1732): Indicator-Sound-DEBUG: indicator-sound: new_voip_slider_widget
(xfce4-indicator-plugin:1732): Indicator-Me-DEBUG: entry hint: Post message...
(xfce4-indicator-plugin:1732): Indicator-Me-DEBUG: entry_maybe_show_hint, nothing in the entry or not focused, so setting the hint to: Post message...

(xfce4-indicator-plugin:1732): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.28.6/./gobject/gsignal.c:2275: signal `destroy' is invalid for instance `0x7fd8f1574a40'
(xfce4-indicator-plugin:1732): Indicator-Session-DEBUG: Username width 45px
(xfce4-indicator-plugin:1732): Indicator-Session-DEBUG: Font size 10.000000 pt
(xfce4-indicator-plugin:1732): Indicator-Session-DEBUG: Screen DPI 96.000000
(xfce4-indicator-plugin:1732): Indicator-Session-DEBUG: Username width 3.375000em
** (xfce4-indicator-plugin:1732): DEBUG: set_icon(nm-no-connection)
(xfce4-indicator-plugin:1732): Indicator-Me-DEBUG: Get the username
(xfce4-indicator-plugin:1732): Indicator-Me-DEBUG: Get the status icon
(xfce4-indicator-plugin:1732): Indicator-Me-DEBUG: Updating username label
(xfce4-indicator-plugin:1732): Indicator-Appmenu-DEBUG: Registering window ID 18874371 with path /com/canonical/menu/1200003 from :1.52
(xfce4-indicator-plugin:1732): Indicator-Appmenu-DEBUG: Creating new windows menu: 1200003, :1.52, /com/canonical/menu/1200003
(xfce4-indicator-plugin:1732): Indicator-Appmenu-DEBUG: Active window is: NULL
(xfce4-indicator-plugin:1732): Indicator-Appmenu-DEBUG: Switching to menus from XID 0
(xfce4-indicator-plugin:1732): Indicator-Appmenu-DEBUG: Looking for parent window on XID 60817411
(xfce4-indicator-plugin:1732): Indicator-Appmenu-DEBUG: Switching to menus from XID 60817411
(xfce4-indicator-plugin:1732): Indicator-Appmenu-DEBUG: Unable to get MWM functions for: 60817411
(xfce4-indicator-plugin:1732): Indicator-Appmenu-DEBUG: Registering window ID 60817411 with path /com/canonical/menu/3A00003 from :1.89
(xfce4-indicator-plugin:1732): Indicator-Appmenu-DEBUG: Creating new windows menu: 3A00003, :1.89, /com/canonical/menu/3A00003
(xfce4-indicator-plugin:1732): Indicator-Appmenu-DEBUG: Switching to menus from XID 60817411
(xfce4-indicator-plugin:1732): Indicator-Appmenu-DEBUG: Switching to menus from desktop
(xfce4-indicator-plugin:1732): Indicator-Appmenu-DEBUG: Active window is: NULL
(xfce4-indicator-plugin:1732): Indicator-Appmenu-DEBUG: Switching to menus from XID 0
(xfce4-indicator-plugin:1732): Indicator-Appmenu-DEBUG: Looking for parent window on XID 60817749
(xfce4-indicator-plugin:1732): Indicator-Appmenu-DEBUG: Switching to menus from XID 60817749
(xfce4-indicator-plugin:1732): Indicator-Appmenu-DEBUG: Unable to get MWM functions for: 60817749
(xfce4-indicator-plugin:1732): Indicator-Appmenu-DEBUG: Registering window ID 60817749 with path /com/canonical/menu/3A00155 from :1.89
(xfce4-indicator-plugin:1732): Indicator-Appmenu-DEBUG: Creating new windows menu: 3A00155, :1.89, /com/canonical/menu/3A00155
(xfce4-indicator-plugin:1732): Indicator-Appmenu-DEBUG: Switching to menus from XID 60817749
(xfce4-indicator-plugin:1732): Indicator-Appmenu-DEBUG: Unregistering: 50331652

(xfce4-indicator-plugin:1732): Indicator-Application-WARNING **: Unable to get application list: Timeout was reached
(xfce4-indicator-plugin:1732): Indicator-Appmenu-DEBUG: Switching to menus from XID 60817411
(xfce4-indicator-plugin:1732): Indicator-Appmenu-DEBUG: Unable to get MWM functions for: 60817411
(xfce4-indicator-plugin:1732): Indicator-Appmenu-DEBUG: Active window is: NULL
(xfce4-indicator-plugin:1732): Indicator-Appmenu-DEBUG: Switching to menus from XID 0

(xfce4-indicator-plugin:1732): GLib-GObject-WARNING **: g_object_weak_unref: couldn't find weak ref 0x7fd8df8eb5e0(0x7fd8f13416c0)
(xfce4-indicator-plugin:1732): Indicator-Appmenu-DEBUG: Switching to menus from XID 60817749
(xfce4-indicator-plugin:1732): Indicator-Appmenu-DEBUG: Unable to get MWM functions for: 60817749
(xfce4-indicator-plugin:1732): Indicator-Appmenu-DEBUG: Registering window ID 67108868 with path /com/canonical/menu/4000004 from :1.95
(xfce4-indicator-plugin:1732): Indicator-Appmenu-DEBUG: Creating new windows menu: 4000004, :1.95, /com/canonical/menu/4000004
(xfce4-indicator-plugin:1732): Indicator-Appmenu-DEBUG: Switching to menus from XID 60817749
(xfce4-indicator-plugin:1732): Indicator-Appmenu-DEBUG: Active window is: NULL
(xfce4-indicator-plugin:1732): Indicator-Appmenu-DEBUG: Switching to menus from XID 0
(xfce4-indicator-plugin:1732): Indicator-Appmenu-DEBUG: Switching to menus from XID 67108868
(xfce4-indicator-plugin:1732): Indicator-Appmenu-DEBUG: Unable to get MWM functions for: 67108868

(xfce4-indicator-plugin:1732): GLib-CRITICAL **: g_variant_get_string: assertion `value != NULL' failed

(xfce4-indicator-plugin:1732): GLib-GIO-CRITICAL **: g_themed_icon_new_with_default_fallbacks: assertion `iconname != NULL' failed

(xfce4-indicator-plugin:1732): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
(xfce4-indicator-plugin:1732): Indicator-Appmenu-DEBUG: Unregistering: 60817411
(xfce4-indicator-plugin:1732): Indicator-Appmenu-DEBUG: Removing menus for 60817411

```

---

### Post by Toz on 2011-08-31
> (xfce4-indicator-plugin:1732): GLib-CRITICAL **: g_strv_length: assertion `str_array != NULL' failed
(xfce4-indicator-plugin:1732): xfce4-indicator-plugin-DEBUG: Looking at Module: libme.so
(xfce4-indicator-plugin:1732): xfce4-indicator-plugin-DEBUG: Loading Module: libme.so
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/blueman/plugins/AppletPlugin.py", line 105, in _load
    self.on_load(applet)
  File "/usr/lib/python2.7/dist-packages/blueman/plugins/applet/PulseAudio.py", line 115, in on_load
    if int(version.split(".")[2]) < 15:
ValueError: invalid literal for int() with base 10: '22-24-g67d18'

Looks like the bluetooth indicator is crashing. Do you use bluetooth? Have you been configuring it lately?

---

### Post by Luke Kijanovich on 2011-08-31
That's very strange, considering that i haven't been using bluetooth for at least a month.

---

### Post by Toz on 2011-08-31
As a test, try uninstalling the **blueman** package to see if it solves the problem. If it does, try re-installing and see what happens.

---

### Post by Luke Kijanovich on 2011-08-31
Nope, problem is still there. I tried running panel from terminal and here's output:
```

(xfce4-indicator-plugin:2749): GLib-CRITICAL **: g_strv_length: assertion `str_array != NULL' failed
(xfce4-indicator-plugin:2749): xfce4-indicator-plugin-DEBUG: Looking at Module: libme.so
(xfce4-indicator-plugin:2749): xfce4-indicator-plugin-DEBUG: Loading Module: libme.so
(xfce4-indicator-plugin:2749): xfce4-indicator-plugin-DEBUG: Looking at Module: libsession.so
(xfce4-indicator-plugin:2749): xfce4-indicator-plugin-DEBUG: Loading Module: libsession.so
(xfce4-indicator-plugin:2749): xfce4-indicator-plugin-DEBUG: Looking at Module: libnetworkmenu.so
(xfce4-indicator-plugin:2749): xfce4-indicator-plugin-DEBUG: Loading Module: libnetworkmenu.so
** (xfce4-indicator-plugin:2749): DEBUG: get_menu()

(xfce4-indicator-plugin:2749): libindicator-WARNING **: IndicatorObject class does not have an accessible description.
(xfce4-indicator-plugin:2749): xfce4-indicator-plugin-DEBUG: Looking at Module: libapplication.so
(xfce4-indicator-plugin:2749): xfce4-indicator-plugin-DEBUG: Loading Module: libapplication.so
(xfce4-indicator-plugin:2749): xfce4-indicator-plugin-DEBUG: Looking at Module: libappmenu.so
(xfce4-indicator-plugin:2749): xfce4-indicator-plugin-DEBUG: Loading Module: libappmenu.so

(xfce4-indicator-plugin:2749): Indicator-Appmenu-WARNING **: Unable to find the file menu stock item
(xfce4-indicator-plugin:2749): Indicator-Appmenu-DEBUG: New Desktop Window: 1800003
(xfce4-indicator-plugin:2749): xfce4-indicator-plugin-DEBUG: Looking at Module: libsoundmenu.so
(xfce4-indicator-plugin:2749): xfce4-indicator-plugin-DEBUG: Loading Module: libsoundmenu.so
GLib-GIO-Message: Using the 'memory' GSettings backend.  Your settings will not be saved or shared with other applications.

(xfce4-indicator-plugin:2749): libindicator-WARNING **: IndicatorObject class does not have an accessible description.
(xfce4-indicator-plugin:2749): xfce4-indicator-plugin-DEBUG: Looking at Module: libmessaging.so
(xfce4-indicator-plugin:2749): xfce4-indicator-plugin-DEBUG: Loading Module: libmessaging.so

(xfce4-indicator-plugin:2749): libindicator-WARNING **: IndicatorObject class does not have an accessible description.

(xfce4-indicator-plugin:2749): libxfce4panel-CRITICAL **: IA__xfce_panel_plugin_add_action_widget: assertion `GTK_IS_WIDGET (widget)' failed
(xfce4-indicator-plugin:2749): Indicator-Appmenu-DEBUG: Registering window ID 18874371 with path /com/canonical/menu/1200003 from :1.60
(xfce4-indicator-plugin:2749): Indicator-Appmenu-DEBUG: Creating new windows menu: 1200003, :1.60, /com/canonical/menu/1200003
(xfce4-indicator-plugin:2749): Indicator-Appmenu-DEBUG: Looking for parent window on XID 69214535
(xfce4-indicator-plugin:2749): Indicator-Appmenu-DEBUG: Switching to menus from XID 69214535
(xfce4-indicator-plugin:2749): Indicator-Appmenu-DEBUG: Unable to get MWM functions for: 69214535
(xfce4-indicator-plugin:2749): Indicator-Appmenu-DEBUG: Registering window ID 69214535 with path /com/canonical/menu/4202147 from :1.83
(xfce4-indicator-plugin:2749): Indicator-Appmenu-DEBUG: Creating new windows menu: 4202147, :1.83, /com/canonical/menu/4202147
(xfce4-indicator-plugin:2749): Indicator-Appmenu-DEBUG: Switching to menus from XID 69214535
(xfce4-indicator-plugin:2749): Indicator-Appmenu-DEBUG: Registering window ID 69206020 with path /com/canonical/menu/4200004 from :1.83
(xfce4-indicator-plugin:2749): Indicator-Appmenu-DEBUG: Creating new windows menu: 4200004, :1.83, /com/canonical/menu/4200004
(xfce4-indicator-plugin:2749): Indicator-Appmenu-DEBUG: Switching to menus from XID 69214535
(xfce4-indicator-plugin:2749): Indicator-Application-DEBUG: Connected to Application Indicator Service.
(xfce4-indicator-plugin:2749): Indicator-Me-DEBUG: entry hint: Post message...
(xfce4-indicator-plugin:2749): Indicator-Me-DEBUG: entry_maybe_show_hint, nothing in the entry or not focused, so setting the hint to: Post message...

(xfce4-indicator-plugin:2749): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.28.6/./gobject/gsignal.c:2275: signal `destroy' is invalid for instance `0x7f65b7156730'
(xfce4-indicator-plugin:2749): Indicator-Sound-DEBUG: indicator-sound: new_volume_slider_widget
(xfce4-indicator-plugin:2749): Indicator-Sound-DEBUG: indicator-sound: new_voip_slider_widget
(xfce4-indicator-plugin:2749): Indicator-Session-DEBUG: Username width 45px
(xfce4-indicator-plugin:2749): Indicator-Session-DEBUG: Font size 10.000000 pt
(xfce4-indicator-plugin:2749): Indicator-Session-DEBUG: Screen DPI 96.000000
(xfce4-indicator-plugin:2749): Indicator-Session-DEBUG: Username width 3.375000em
** (xfce4-indicator-plugin:2749): DEBUG: new_tech_menuitem()
** (xfce4-indicator-plugin:2749): DEBUG: new_tech_menuitem()
(xfce4-indicator-plugin:2749): Indicator-Messages-DEBUG: new_application_item ("Set Up Broadcast Account...")
(xfce4-indicator-plugin:2749): Indicator-Messages-DEBUG: new_application_item ("Ubuntu One")
(xfce4-indicator-plugin:2749): Indicator-Application-DEBUG: Request current apps
(xfce4-indicator-plugin:2749): Indicator-Me-DEBUG: Get the username
(xfce4-indicator-plugin:2749): Indicator-Me-DEBUG: Get the status icon
(xfce4-indicator-plugin:2749): Indicator-Me-DEBUG: Updating username label
** (xfce4-indicator-plugin:2749): DEBUG: set_icon(nm-no-connection)
(xfce4-indicator-plugin:2749): Indicator-Appmenu-DEBUG: Registering window ID 50331652 with path /com/canonical/menu/3000004 from :1.132
(xfce4-indicator-plugin:2749): Indicator-Appmenu-DEBUG: Creating new windows menu: 3000004, :1.132, /com/canonical/menu/3000004
(xfce4-indicator-plugin:2749): Indicator-Appmenu-DEBUG: Switching to menus from XID 69214535

```

---

### Post by Toz on 2011-09-01
Try moving the existing panel configuration files and trying with a fresh config.

```
mv ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-panel.xml ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-panel.xml.bak

mv ~/.config/xfce4/panel ~/.config/xfce4/panel.bak

cp -r /etc/xdg/xdg-xubuntu/xfce4/panel ~/.config/xfce4
```

---

### Post by Luke Kijanovich on 2011-09-01
Nope, still not there. I tried re-installing plugin, that didn't work out. Instead, it deleted my network configuration, so now i can't even connect to the internet. :(

---

### Post by Toz on 2011-09-01
Sorry, I left out an important step in post #9. You should probably log out first, type Ctrl-Atl-F1 to go to the first terminal, log in there to a command prompt, then make those changes. That way the current session state won't affect your changes. When done, Ctrl-Alt-F7 to get backto the gui then log in.

---

### Post by Luke Kijanovich on 2011-09-04
I solved it by re-installing xfce4-panel. Anyway, thanks for your help.

---

### Post by maclinux on 2011-09-25
hi. running 11.04 and i got a prob with the sound label in the upper right corner. does not load on startup as well as the sound prefs.  I got 2 picts to make it underst better the whole situat.  Weird is that the sound is working but i have no control over it.  What a tease hum?

Appreciate your help and thanks in advanced.

Renato

---

