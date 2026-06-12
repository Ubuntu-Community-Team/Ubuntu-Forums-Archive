---
title: "gwibber &amp; rhythmbox"
date: 2012-04-08
forum: Desktop Environments
---

### Post by huynhhuuhieu on 2012-04-08
gwibber and rhythmbox run with some wrong at few functions
I run them via terminal
but i don't understand these code, could you help me
```
huynhhuuhieu@huynhhuuhieu:~$ gwibber

(gwibber:1975): Gtk-CRITICAL **: gtk_radio_button_set_group: assertion `!g_slist_find (group, radio_button)' failed

(gwibber:1975): Gtk-CRITICAL **: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed
Loading plugin for identica
Loading plugin for facebook
Loading plugin for twitter
huynhhuuhieu@huynhhuuhieu:~$ rhythmbox
Sense key: 0x72 0x0b 0x47 0x00 0x00 0x00 0x00 0x0e 0x09 0x0c 0x00 0x00 0x00 0x02 0x00 0x00 0x00 0x00 0x00 

** (rhythmbox:2301): WARNING **: Error calling get_info: Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/service.py", line 707, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/platform/linux/dbus_interface.py", line 707, in get_info
    return self.service.folders.get_info(path)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/syncdaemon/interaction_interfaces.py", line 156, in inner
    result = f(*new_args, **new_kwargs)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/logger.py", line 269, in inner
    res = f(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/syncdaemon/interaction_interfaces.py", line 707, in get_info
    mdobj = self.fs_manager.get_by_path(path)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/syncdaemon/filesystem_manager.py", line 780, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/huynhhuuhieu/.ubuntuone/Purchased from Ubuntu One'


** (rhythmbox:2301): CRITICAL **: syncdaemon_folder_info_get_subscribed: assertion `SYNCDAEMON_IS_FOLDER_INFO (finfo)' failed

(rhythmbox:2301): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

```

---

### Post by Paddy Landau on 2012-04-09
Sometimes, GUI programs will display error messages on a terminal. Normally you don't need to worry about them.

If gwibber and rhythmbox are running all right, then ignore the error messages.

If they do cause problems, you need to tell us what is happening.

---

