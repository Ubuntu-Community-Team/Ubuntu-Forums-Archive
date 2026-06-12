---
title: "loading gnome desktop"
date: 2013-05-08
forum: Desktop Environments
---

### Post by shgn on 2013-05-08
I install ubuntu 12.04 and update all packages and add gnome repository and install gnome-shell, but when i logout and wnat to select the gnome desktop in login screen, i just have gnome classic and gnome classc(no effects) options to select and there is no gnome.
what is the problem? how to solve it?:confused:
and when i run
```

sudo gnome-shell --replace

```
i got:
```

Window manager warning: Log level 16: Error getting session for the process we are in: GDBus.Error:org.freedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '3413' (g-io-error-quark 36)
    JS ERROR: !!!   Exception was: Error: Must pass a single argument to log()
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = '"gjs_throw"'
    JS ERROR: !!!     stack = '"("Must pass a single argument to log()")@gjs_throw:0
([object _private_Gio_DBusProxy],[object _private_Gio_SimpleAsyncResult])@/usr/share/gjs-1.0/overrides/Gio.js:150
"'
    JS ERROR: !!!     message = '"Must pass a single argument to log()"'

(gnome-shell:3413): folks-WARNING **: Failed to find primary PersonaStore with type ID 'eds' and ID 'system'.
Individuals will not be linked properly and creating new links between Personas will not work.
The configured primary PersonaStore's backend may not be installed. If you are unsure, check with your distribution.
SendMessage (54525985, 0x101f, (nil), (nil))
SendMessage (0, 0x1203, (nil), 0xbfc95920)
SendMessage (0, 0x1204, (nil), 0xbfc95920)
SendMessage (0, 0x1203, 0x1, 0xbfc95920)
SendMessage (0, 0x1204, 0x1, 0xbfc95920)
SendMessage (0, 0x1203, 0x2, 0xbfc95920)
SendMessage (0, 0x1204, 0x2, 0xbfc95920)
SendMessage (0, 0x1203, 0x3, 0xbfc95920)
SendMessage (0, 0x1204, 0x3, 0xbfc95920)
SendMessage (0, 0x1203, 0x4, 0xbfc95920)
SendMessage (0, 0x1204, 0x4, 0xbfc95920)
SendMessage (54525985, 0x101f, (nil), (nil))
SendMessage (0, 0x1203, (nil), 0xbfc96440)
SendMessage (0, 0x1204, (nil), 0xbfc96440)
SendMessage (0, 0x1203, 0x1, 0xbfc96440)
SendMessage (0, 0x1204, 0x1, 0xbfc96440)
SendMessage (0, 0x1203, 0x2, 0xbfc96440)
SendMessage (0, 0x1204, 0x2, 0xbfc96440)
SendMessage (0, 0x1203, 0x3, 0xbfc96440)
SendMessage (0, 0x1204, 0x3, 0xbfc96440)
SendMessage (0, 0x1203, 0x4, 0xbfc96440)
SendMessage (0, 0x1204, 0x4, 0xbfc96440)
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3400012 (KeePass Pa)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Log level 8: meta_window_raise: assertion `!window->override_redirect' failed
Window manager warning: Log level 8: meta_window_focus: assertion `!window->override_redirect' failed
Window manager warning: Window 0x3400070 (Open Datab) sets an MWM hint indicating it isn't resizable, but sets min size 104 x 1 and max size 486 x 228; this doesn't make much sense.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3400070 (Open Datab)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3400070 (Open Datab)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3400012 (MyPassWord)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Window 0x3400a7d (Edit Entry) sets an MWM hint indicating it isn't resizable, but sets min size 104 x 1 and max size 568 x 523; this doesn't make much sense.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3400a7d (Edit Entry)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3400a7d (Edit Entry)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3400012 (MyPassWord)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

```

---

### Post by markbl on 2013-05-08
When you say "add gnome repository" what exactly did you add?

---

### Post by shgn on 2013-05-11
I added 

```
sudo add-apt-repository ppa:gnome3-team/gnome3
```

---

### Post by Frogs Hair on 2013-05-11
The Gnome Shell is in the software center , and the ppa is optional and use at your own risk. There should have been three commands needed to properly install the ppa , so check the instructions you used. 

They might look like this.


```
sudo add-apt-repository ppa:gnome3-team/gnome3
```

```
sudo apt-get update
```

```
sudo apt-get install gnome-shell
```

---

### Post by markbl on 2013-05-11
Should also make sure you actually upgrade all the GNOME stuff:
```

sudo apt-get dist-upgrade

```
The reboot and log in to GNOME.

---

