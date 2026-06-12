---
title: "D600 Feisty Beryl"
date: 2007-04-18
forum: Desktop Environments
---

### Post by cornish on 2007-04-18
I have done some searching but none of the posts seem to answer my problem

I have a Dell D600 (very popular) witch Feisty installed :)

I have followed the instructions to the letter

when I log out and select XGL from the sessions it dosnt login and returns an error message

Fatal Server Error no screens found

When I reboot the PC X-Server crashes and I have to edit /etc/X11/xor.conf changing Driver "fglrx" back to "ati"

Can any one help?

```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "mark"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/nb10001L:/tmp/.ICE-unix/5321
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Starting gdesklets-daemon...

Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]evolution-alarm-notify-Message: Setting timeout for 6227 1176854400 1176848173
evolution-alarm-notify-Message:  Wed Apr 18 01:00:00 2007

evolution-alarm-notify-Message:  Tue Apr 17 23:16:13 2007


Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]Initializing gnome-mount extension

Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]alarm-notify.c:368 (alarm_notify_new) - Alarm Notify New 
 alarm-notify.c:304 (alarm_channel_setup) - Channel Setup
 alarm-notify.c:243 (alarm_notify_init) - Initing Alarm Notify
alarm-queue.c:1875 (alarm_queue_init)
alarm-queue.c:218 (queue_midnight_refresh) - Refresh at Wed Apr 18 01:00:00 2007
 
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/mark/.evolution/calendar/local/system 
alarm-notify.c:456 (alarm_notify_add_calendar) file:///home/mark/.evolution/calendar/local/system - Calendar Open Async... 0x80b9ac0
alarm-notify.c:220 (load_calendars) - Loading Calendar contacts:/// 
alarm-notify.c:456 (alarm_notify_add_calendar) contacts:/// - Calendar Open Async... 0x80d2900
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/mark/.evolution/tasks/local/system 
alarm-notify.c:456 (alarm_notify_add_calendar) file:///home/mark/.evolution/tasks/local/system - Calendar Open Async... 0x80d2940
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/mark/.evolution/me
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]mos/local/system 
alarm-notify.c:456 (alarm_notify_add_calendar) file:///home/mark/.evolution/memos/local/system - Calendar Open Async... 0x80d6260
alarm-notify.c:393 (cal_opened_cb) file:///home/mark/.evolution/calendar/local/system - Calendar Status 0
alarm-queue.c:2057 (alarm_queue_add_client) - Posting a task
alarm-notify.c:349 (alarm_msg_received) - 0x80ce550: Received at thread b5d67b90
alarm-queue.c:2008 (alarm_queue_add_async) - 0x80b9ac0
alarm-queue.c:560 (load_alarms_for_today) - From Tue Apr 17 23:16:21 2007
 to Tue Apr 17 23:16:21 2007

alarm-queue.c:497 (load_alarms) 
alarm-queue.c:526 (load_alarms) - Setting Call backs 
alarm-notify.c:337 (alarm_msgport_replied) - 0x80ce550: Replied to GUI thread
alarm-notify.c:393 (cal_opened_cb) file:///home/mark/.evolution/tasks/local/system - Calendar Status 0
alarm-queue.c:2057 (alarm_queue_add_client) - Posting a task
alarm-notify.c:349 (alarm_msg_received) - 0x80d5ea0: Received at thread b5d67b90
alarm-queue.c:2008 (alarm_queue_add_async) - 0x80d2940
alar
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]m-queue.c:560 (load_alarms_for_today) - From Tue Apr 17 23:16:21 2007
 to Tue Apr 17 23:16:21 2007

alarm-queue.c:497 (load_alarms) 
alarm-queue.c:526 (load_alarms) - Setting Call backs 
alarm-notify.c:337 (alarm_msgport_replied) - 0x80d5ea0: Replied to GUI thread
alarm-notify.c:393 (cal_opened_cb) file:///home/mark/.evolution/memos/local/system - Calendar Status 0
alarm-queue.c:2057 (alarm_queue_add_client) - Posting a task
alarm-notify.c:349 (alarm_msg_received) - 0x80d9938: Received at thread b5d67b90
alarm-queue.c:2008 (alarm_queue_add_async) - 0x80d6260
alarm-queue.c:560 (load_alarms_for_today) - From Tue Apr 17 23:16:21 2007
 to Tue Apr 17 23:16:21 2007

alarm-queue.c:497 (load_alarms) 
alarm-queue.c:526 (load_alarms) - Setting Call backs 
alarm-notify.c:337 (alarm_msgport_replied) - 0x80d9938: Replied to GUI thread
alarm-notify.c:393 (cal_opened_cb) contacts:/// - Calendar Status 0
alarm-queue.c:2057 (alarm_queue_add_client) - Posting a task
alarm-notify.c:349 (alarm_msg_received) - 0x80d79f0: Received
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
                                        
Connected to daemon in 16612 milliseconds.

** (gnome-app-install:5722): WARNING **: return value of custom widget handler was not a GtkWidget
/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py:1532: GtkWarning: gtk_tree_model_sort_sort: assertion `tree_model_sort->default_sort_func != NULL' failed
  item.applications.set_default_sort_func(None)
Window manager warning: Window 0x3008802 () sets an MWM hint indicating it isn't resizable, but sets min size 486 x 269 and max size 2147483647 x 2147483647; this doesn't make much sense.
Window manager warning: Window 0x3008802 () sets an MWM hint indicating it isn't resizable, but sets min size 486 x 269 and max size 2147483647 x 2147483647; this doesn't make much sense.
Window manager warning: Window 0x3008f3e () sets an MWM hint indicating it isn't resizable, but sets min size 486 x 269 and max size 2147483647 x 2147483647; this doesn't make much sense.
Window manager warning: Window 0x3008f3e () sets an MWM hint indicating it isn't resizable, but sets min size 486 x 269 and max size 2147483647 x 2147483647; this doesn't make much sense.
sh: disown: not found
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_param_spec_boxed: assertion `G_TYPE_IS_BOXED (boxed_type)' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_object_class_install_property: assertion `G_IS_PARAM_SPEC (pspec)' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_param_spec_boxed: assertion `G_TYPE_IS_BOXED (boxed_type)' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_object_class_install_property: assertion `G_IS_PARAM_SPEC (pspec)' failed
Create program-folder
Create thumbnail-folder
Create temp-folder
Create download-folder
Create backgrounds-folder
Create splashscreens-folder
Create themes-folder
/usr/share/themes/LegacyHuman/gtk-2.0/gtkrc:55: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/usr/share/themes/LegacyHuman/gtk-2.0/gtkrc:56: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/usr/share/themes/LegacyHuman/gtk-2.0/gtkrc:57: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/usr/lib/ruby/1.8/gnome-art/gnome_art.rb:132: warning: GRClosure invoking callback: already destroyed
/usr/lib/ruby/1.8/gnome-art/gnome_art.rb:132: [BUG] Segmentation fault
ruby 1.8.5 (2006-08-25) [i486-linux]

/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_param_spec_boxed: assertion `G_TYPE_IS_BOXED (boxed_type)' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_object_class_install_property: assertion `G_IS_PARAM_SPEC (pspec)' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_param_spec_boxed: assertion `G_TYPE_IS_BOXED (boxed_type)' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_object_class_install_property: assertion `G_IS_PARAM_SPEC (pspec)' failed
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
/usr/bin/gnome-btdownload:858: GtkDeprecationWarning: gtk.threads_init is deprecated, use gtk.gdk.threads_init instead
  gtk.threads_init()
/usr/bin/gnome-btdownload:1055: GtkDeprecationWarning: gtk.threads_enter is deprecated, use gtk.gdk.threads_enter instead
  gtk.threads_enter()
/usr/bin/gnome-btdownload:1060: GtkDeprecationWarning: gtk.threads_leave is deprecated, use gtk.gdk.threads_leave instead
  gtk.threads_leave()
/usr/bin/gnome-btdownload:1154: GtkDeprecationWarning: gtk.threads_enter is deprecated, use gtk.gdk.threads_enter instead
  gtk.threads_enter()
/usr/bin/gnome-btdownload:1159: GtkDeprecationWarning: gtk.threads_leave is deprecated, use gtk.gdk.threads_leave instead
  gtk.threads_leave()
/usr/bin/gnome-btdownload:1080: GtkDeprecationWarning: gtk.threads_enter is deprecated, use gtk.gdk.threads_enter instead
  gtk.threads_enter()
/usr/bin/gnome-btdownload:1122: GtkDeprecationWarning: gtk.threads_leave is deprecated, use gtk.gdk.threads_leave instead
  gtk.threads_leave()
/usr/bin/gnome-btdownload:1164: GtkDeprecationWarning: gtk.threads_enter is deprecated, use gtk.gdk.threads_enter instead
  gtk.threads_enter()
/usr/bin/gnome-btdownload:1185: GtkDeprecationWarning: gtk.threads_leave is deprecated, use gtk.gdk.threads_leave instead
  gtk.threads_leave()
/usr/lib/ruby/1.8/open-uri.rb: line 211
   Gtk-WARNING **:Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand isn't supposed to be an entity, escape it as &amp;
/usr/lib/ruby/1.8/open-uri.rb: line 211
   Gtk-WARNING **:Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand isn't supposed to be an entity, escape it as &amp;
/usr/lib/ruby/1.8/open-uri.rb: line 211
   Gtk-WARNING **:Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand isn't supposed to be an entity, escape it as &amp;
/usr/lib/ruby/1.8/open-uri.rb: line 211
   Gtk-WARNING **:Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand isn't supposed to be an entity, escape it as &amp;
/usr/lib/ruby/1.8/open-uri.rb: line 211
   Gtk-WARNING **:Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand isn't supposed to be an entity, escape it as &amp;
/usr/lib/ruby/1.8/open-uri.rb: line 211
   Gtk-WARNING **:Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand isn't supposed to be an entity, escape it as &amp;
/usr/lib/ruby/1.8/rexml/encoding.rb: line 47
   Gtk-WARNING **:Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand isn't supposed to be an entity, escape it as &amp;
/usr/lib/ruby/1.8/rexml/encoding.rb: line 47
   Gtk-WARNING **:Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand isn't supposed to be an entity, escape it as &amp;
/usr/lib/ruby/1.8/rexml/encoding.rb: line 47
   Gtk-WARNING **:Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand isn't supposed to be an entity, escape it as &amp;
/usr/lib/ruby/1.8/rexml/encoding.rb: line 47
   Gtk-WARNING **:Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand isn't supposed to be an entity, escape it as &amp;
/usr/lib/ruby/1.8/rexml/encoding.rb: line 47
   Gtk-WARNING **:Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand isn't supposed to be an entity, escape it as &amp;
/usr/lib/ruby/1.8/rexml/encoding.rb: line 47
   Gtk-WARNING **:Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand isn't supposed to be an entity, escape it as &amp;
/usr/lib/ruby/1.8/rexml/encoding.rb: line 47
   Gtk-WARNING **:Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand isn't supposed to be an entity, escape it as &amp;
/usr/lib/ruby/1.8/rexml/encoding.rb: line 47
   Gtk-WARNING **:Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand isn't supposed to be an entity, escape it as &amp;
/usr/lib/ruby/1.8/rexml/encoding.rb: line 47
   Gtk-WARNING **:Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand isn't supposed to be an entity, escape it as &amp;
/usr/lib/ruby/1.8/rexml/encoding.rb: line 47
   Gtk-WARNING **:Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand isn't supposed to be an entity, escape it as &amp;
/usr/lib/ruby/1.8/rexml/encoding.rb: line 47
   Gtk-WARNING **:Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand isn't supposed to be an entity, escape it as &amp;
/usr/lib/ruby/1.8/rexml/encoding.rb: line 47
   Gtk-WARNING **:Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand isn't supposed to be an entity, escape it as &amp;
/usr/lib/ruby/1.8/rexml/encoding.rb: line 47
   Gtk-WARNING **:Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand isn't supposed to be an entity, escape it as &amp;
/usr/lib/ruby/1.8/rexml/encoding.rb: line 47
   Gtk-WARNING **:Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand isn't supposed to be an entity, escape it as &amp;
/usr/lib/ruby/1.8/rexml/encoding.rb: line 47
   Gtk-WARNING **:Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand isn't supposed to be an entity, escape it as &amp;
/usr/lib/ruby/1.8/rexml/encoding.rb: line 47
   Gtk-WARNING **:Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand isn't supposed to be an entity, escape it as &amp;
/usr/lib/ruby/1.8/rexml/encoding.rb: line 47
   Gtk-WARNING **:Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand isn't supposed to be an entity, escape it as &amp;
/usr/lib/ruby/1.8/rexml/encoding.rb: line 47
   Gtk-WARNING **:Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand isn't supposed to be an entity, escape it as &amp;
/usr/lib/ruby/1.8/rexml/encoding.rb: line 47
   Gtk-WARNING **:Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand isn't supposed to be an entity, escape it as &amp;
/usr/lib/ruby/1.8/rexml/encoding.rb: line 47
   Gtk-WARNING **:Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand isn't supposed to be an entity, escape it as &amp;
/usr/lib/ruby/1.8/rexml/encoding.rb: line 47
   Gtk-WARNING **:Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand isn't supposed to be an entity, escape it as &amp;
/usr/lib/ruby/1.8/rexml/encoding.rb: line 47
   Gtk-WARNING **:Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand isn't supposed to be an entity, escape it as &amp;
/usr/lib/ruby/1.8/gnome-art/gnome_art.rb:132: warning: GRClosure invoking callback: already destroyed
/usr/lib/ruby/1.8/gnome-art/gnome_art.rb:132: warning: GRClosure invoking callback: already destroyed
/usr/lib/ruby/1.8/gnome-art/gnome_art.rb:132: warning: GRClosure invoking callback: already destroyed
/usr/bin/gnome-btdownload:1128: GtkDeprecationWarning: gtk.threads_enter is deprecated, use gtk.gdk.threads_enter instead
  gtk.threads_enter()
/usr/bin/gnome-btdownload:1142: GtkDeprecationWarning: gtk.threads_leave is deprecated, use gtk.gdk.threads_leave instead
  gtk.threads_leave()
sh: disown: not found
Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager.
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Support for non power of two textures missing
**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : failed

beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager.
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
/usr/bin/compiz.real: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real: Failed to manage screen: 0
/usr/bin/compiz.real: No manageable screens found on display :0.0
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Write fault on path [Unknown]
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_param_spec_boxed: assertion `G_TYPE_IS_BOXED (boxed_type)' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_object_class_install_property: assertion `G_IS_PARAM_SPEC (pspec)' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_param_spec_boxed: assertion `G_TYPE_IS_BOXED (boxed_type)' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_object_class_install_property: assertion `G_IS_PARAM_SPEC (pspec)' failed
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
Reusing existing ksycoca
kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
kio (KSycoca): ERROR: No database available!
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x4d specified for 0x3200028 (Invitation).
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x3200012 specified for 0x3200027 (Remote Des).
/usr/share/themes/LegacyHuman/gtk-2.0/gtkrc:55: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/usr/share/themes/LegacyHuman/gtk-2.0/gtkrc:56: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/usr/share/themes/LegacyHuman/gtk-2.0/gtkrc:57: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
evolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1176854400
 at thread b5d67b90
alarm-queue.c:2008 (alarm_queue_add_async) - 0x80d2900
alarm-queue.c:560 (load_alarms_for_today) - From Tue Apr 17 23:16:22 2007
 to Tue Apr 17 23:16:22 2007

alarm-queue.c:497 (load_alarms) 
alarm-queue.c:526 (load_alarms) - Setting Call backs 
alarm-notify.c:337 (alarm_msgport_replied) - 0x80d79f0: Replied to GUI thread
alarm-queue.c:1837 (check_midnight_refresh)
alarm-queue.c:1837 (check_midnight_refresh)
alarm-queue.c:1837 (check_midnight_refresh)
alarm-queue.c:279 (midnight_refresh_cb) - Invoking task for midnight refresh
alarm-notify.c:349 (alarm_msg_received) - 0x80d9a90: Received at thread b5d67b90
alarm-queue.c:249 (midnight_refresh_async) 
alarm-queue.c:233 (add_client_alarms_cb) - Adding (nil)
alarm-queue.c:560 (load_alarms_for_today) - From Wed Apr 18 01:00:01 2007
 to Wed Apr 18 01:00:01 2007

alarm-queue.c:497 (load_alarms) 
alarm-queue.c:516 (load_alarms) - Disconnecting old queries 
alarm-queue.c:526 (load_alarms) - Setting Call backs 
alarm-queue.c:233 (add_client_alarms_cevolution-alarm-notify-Message: alarm.c:235: Requested removal of nonexistent alarm!
b) - Adding (nil)
alarm-queue.c:560 (load_alarms_for_today) - From Wed Apr 18 01:00:01 2007
 to Wed Apr 18 01:00:01 2007

alarm-queue.c:497 (load_alarms) 
alarm-queue.c:516 (load_alarms) - Disconnecting old queries 
alarm-queue.c:526 (load_alarms) - Setting Call backs 
alarm-queue.c:233 (add_client_alarms_cb) - Adding (nil)
alarm-queue.c:560 (load_alarms_for_today) - From Wed Apr 18 01:00:01 2007
 to Wed Apr 18 01:00:01 2007

alarm-queue.c:497 (load_alarms) 
alarm-queue.c:516 (load_alarms) - Disconnecting old queries 
alarm-queue.c:526 (load_alarms) - Setting Call backs 
alarm-queue.c:233 (add_client_alarms_cb) - Adding (nil)
alarm-queue.c:560 (load_alarms_for_today) - From Wed Apr 18 01:00:01 2007
 to Wed Apr 18 01:00:01 2007

alarm-queue.c:497 (load_alarms) 
alarm-queue.c:516 (load_alarms) - Disconnecting old queries 
alarm-queue.c:526 (load_alarms) - Setting Call backs 
alarm-queue.c:256 (midnight_refresh_async) - Reschedule the midnight update 
alarm-queue.c:218 (queue_midnight_refresh) - Refresh at Thu Aevolution-alarm-notify-Message: Setting timeout for 86400 1176940800 1176854400
evolution-alarm-notify-Message:  Thu Apr 19 01:00:00 2007

evolution-alarm-notify-Message:  Wed Apr 18 01:00:00 2007

** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

** (gnome-app-install:13335): WARNING **: return value of custom widget handler was not a GtkWidget
/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py:1532: GtkWarning: gtk_tree_model_sort_sort: assertion `tree_model_sort->default_sort_func != NULL' failed
  item.applications.set_default_sort_func(None)
Window manager warning: Window 0x3a087d7 () sets an MWM hint indicating it isn't resizable, but sets min size 486 x 269 and max size 2147483647 x 2147483647; this doesn't make much sense.
Window manager warning: Window 0x3a087d7 () sets an MWM hint indicating it isn't resizable, but sets min size 486 x 269 and max size 2147483647 x 2147483647; this doesn't make much sense.

(nmapfe:13500): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(nmapfe:13500): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x4d specified for 0x1c001d1 ().
Saving session: gnome-terminal --window-with-profile-internal-id=Default --show-menubar --role=gnome-terminal-8389-404825976-1176852217 --active --geometry 80x24+0+25 --title mark@nb10001L: ~ --working-directory /home/mark --zoom 1 
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus the no_focus_window with a timestamp of 0.  This shouldn't happen!

--- Hash table keys for warning below:
--> ˜NŽ˜£eg</i>
--> À$:///home/mark/crossoveroffic0$

(nautilus:5392): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 2 elements at quit time (keys above)

(evolution-alarm-notify:5423): evolution-alarm-notify-CRITICAL **: alarm_queue_done: assertion `g_hash_table_size (client_alarms_hash) == 0' failed
pr 19 01:00:00 2007
 
alarm-notify.c:337 (alarm_msgport_replied) - 0x80d9a90: Replied to GUI thread
alarm-notify.c:274 (alarm_notify_finalize) - Finalize 
 alarm-notify.c:259 (dequeue_client) - Removing client 0x80b9ac0
 alarm-queue.c:2167 (alarm_queue_remove_client) - Posting a task
alarm-notify.c:259 (dequeue_client) - Removing client 0x80d2900
 alarm-queue.c:2167 (alarm_queue_remove_client) - Posting a task
alarm-notify.c:259 (dequeue_client) - Removing client 0x80d2940
 alarm-queue.c:2167 (alarm_queue_remove_client) - Posting a task
alarm-notify.c:259 (dequeue_client) - Removing client 0x80d6260
 alarm-queue.c:2167 (alarm_queue_remove_client) - Posting a task



```

---

### Post by josephus on 2007-04-18
correct me if I'm wrong but your laptop uses the ati mobility 7500 graphics card?

you won't be able to use the fglrx driver with that chip, but using the ati driver you still should be able to run beryl (at least i can with that chip).

post your xorg.conf

this helped me get things running when i was using edgy, but not sure if it is need in feisty.

[http://ubuntuforums.org/showthread.php?t=361136](http://ubuntuforums.org/showthread.php?t=361136)

---

### Post by cornish on 2007-04-18
Thanks for the quick reply here it is

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
	Driver		"ati"
	#Driver		"fglrx"	
	BusID		"PCI:1:0:0"
EndSection

#Section "Extensions"
#	Option 		"Composite" "false"
#EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

I can load the beryl manager fine, but when I change the display manager to XGL?(Sorry not of the linux box  at the moment) it dosnt do anything and reverts back to GDM

---

### Post by josephus on 2007-04-18
the fglrx support for your card depends on which version you are using.  the support for your card was dropped in one of the newer versions, so it is possible that that is what is causing your problems.   so double check which version you are using and downgrade if necessary.

however, when you are choosing the ati driver in xorg.conf i think your fglrx driver is still being loaded up and is conflicting with the ati/radeon driver.   you need to unload it from memory before running beryl.
```

sudo mobprobe -r fglrx

```
or you can make it permanent by blacklisting at boot time.

---

### Post by cornish on 2007-04-19
I have done modprobe -r fglrx I think you might be right about fglrx not supporting my graphics card but im sure I have seen it working on a Dell D600 before.

---

### Post by josephus on 2007-04-19
and when you run beryl does it still complain?

---

### Post by cornish on 2007-04-20
When I load beryl the icon appears I go to change the window manager to Beryl it flickers tries to change the appearance but then flicks back to what it was.

Does that make sense??

---

### Post by josephus on 2007-04-20
what if you start beryl in terminal,  can you post the output?   (for some reason i have to issue the command twice before it works properly)

---

### Post by cornish on 2007-04-20
Give me a minute

---

### Post by cornish on 2007-04-20
Ok im on the PC now here is the output when I try it from the command

```
**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : failed

Support for non power of two textures missing
beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

```

When I do this I seem to loose all my bars maximize minimize close

After that I typed beryl-manager

```
 Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```

Any clues??

---

### Post by josephus on 2007-04-20
and this is with fglrx disabled?  can you double check your lsmod to see if the module is loaded?

---

### Post by cornish on 2007-04-20
Yes this is with FGLRX disabled

---

### Post by josephus on 2007-04-20
ok.  these open source drivers are getting us anywhere.  maybe try fglrx again.  just need to make sure that we are installing the right version.  

i've read a lot of post where people swear by envy - give that a shot, and select version 8.28.8 (unless you tried that already and it didn't work)

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by cornish on 2007-04-20
Never used envy beofre downloading now what I am installing FGLRX again? or ATI

---

### Post by josephus on 2007-04-20
it's the ati binary drivers == fglrx.

---

### Post by cornish on 2007-04-20
Ok chap I just tried that and xorg went completely tits up

There were two monitors two devices and two screens, couldnt get a gui as it complained about no screens available

---

### Post by josephus on 2007-04-20
is this the same problem that you had before when you were using fglrx?

---

### Post by cornish on 2007-04-20
yes screen not found do I need the fglrx source installed??

---

### Post by josephus on 2007-04-20
is it possible that you still have the previous fglrx drivers installed and that one is taking precedence?

---

### Post by cornish on 2007-04-20
I have just installed

beryl-ubuntu
fglrx-kernel-source im going to envy again because it did moan that the source wasnt there

---

### Post by cornish on 2007-04-20
I thought I would paste a copy of my xorg.conf after running envy I really dont want to restart I know what will happen

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "dbe"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "uk"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    30.0 - 70.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1400x1050"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

```

---

### Post by josephus on 2007-04-20
i was just reading this post: 

[http://ubuntuforums.org/showthread.php?t=354592&highlight=fglrx+radeon+mobility+9000](http://ubuntuforums.org/showthread.php?t=354592&highlight=fglrx+radeon+mobility+9000)

people are having the same problem as you with feisty and the old fglrx driver.

---

### Post by josephus on 2007-04-20
i don't think i'll be able to help you through this problem.  at this point i don't think it's a configuration problem, and sounds more like a bug.  if i were you i would file a bug report and hope it gets fixed in the future.  until then stick with the open source ati drivers

if i run across anything else that might be helpful i'll post a message.

---

### Post by cornish on 2007-04-20
Well that seems to be the case then

---

### Post by SuperAndy on 2007-05-23
just to add extra weight to this, i am having the same problem.

just to clarify though, if i were to use edgy eft instead, i.e. to downgrade, would this sort me out?

and, what are the chances of support being implemented in gutsy gibbon.

and finally, why cant i just sudo-apt get remove the dodgy stuff, and manually download and install the old stuff? or is that not possible?

---

