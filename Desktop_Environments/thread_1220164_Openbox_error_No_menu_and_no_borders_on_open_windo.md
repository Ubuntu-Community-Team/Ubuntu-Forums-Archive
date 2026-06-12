---
title: "Openbox error: No menu and no borders on open windows"
date: 2009-07-22
forum: Desktop Environments
---

### Post by stepper on 2009-07-22
Ok, I'm stumped when I load Openbox everything in autostart.sh loads but the windows of open windows do not have borders and no menu when you right click on the desktop. Can I get some help to fix this?

~/.xsession-errors:
> 
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_ZA.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
** (gnome-volume-control-applet:12672): DEBUG: Disabling debugging
Conky: desktop window (1a7) is root window
Conky: window type - desktop
Conky: drawing to created window (0x1400001)
Conky: drawing to double buffer
Conky: MPD error: host "localhost" not found: Name or service not known

Conky: MPD error: host "localhost" not found: Name or service not known

I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.

(gnome-settings-daemon:12670): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:12670): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
Conky: MPD error: host "localhost" not found: Name or service not known

** (nm-applet:12669): DEBUG: applet_common_device_state_changed
** (nm-applet:12669): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:12669): DEBUG: applet_common_device_state_changed
** (nm-applet:12669): DEBUG: applet_common_device_state_changed
** (nm-applet:12669): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:12669): DEBUG: foo_client_state_changed_cb
Conky: MPD error: host "localhost" not found: Name or service not known

** (nm-applet:12669): DEBUG: applet_common_device_state_changed
Conky: MPD error: host "localhost" not found: Name or service not known

Conky: MPD error: host "localhost" not found: Name or service not known

Conky: MPD error: host "localhost" not found: Name or service not known

[INFO   ] Loading theme 'grey' ..
[INFO   ] Loading plugin 'menu' ..
[DEBUG  ] Menu: can't parse nautilus-autorun-software.desktop
[DEBUG  ] Menu: can't parse gnome-font-viewer.desktop
[DEBUG  ] Menu: can't parse sun-java5-java.desktop
[DEBUG  ] Menu: can't parse seahorse-pgp-encrypted.desktop
[DEBUG  ] Menu: can't parse gmenu-simple-editor.desktop
[DEBUG  ] Menu: can't parse mount-archive.desktop
[DEBUG  ] Menu: can't parse gnome-wm.desktop
[DEBUG  ] Menu: can't parse seahorse-pgp-signature.desktop
[DEBUG  ] Menu: can't parse compiz.desktop
[DEBUG  ] Menu: can't parse nautilus.desktop
[DEBUG  ] Menu: can't parse sun-java6-java.desktop
[DEBUG  ] Menu: can't parse metacity.desktop
[DEBUG  ] Menu: can't parse nautilus-folder-handler.desktop
[DEBUG  ] Menu: can't parse seahorse-pgp-keys.desktop
[INFO   ] Loading plugin 'separator' ..
[INFO   ] Loading plugin 'launcher' ..
[INFO   ] Loading plugin 'separator' ..
[INFO   ] Loading plugin 'showdesktop' ..
[INFO   ] Loading plugin 'pager' ..
[WARNING] Unable to load plugin 'pager': 'NoneType' object has no attribute 'get_number'
Traceback (most recent call last):
  File "/usr/share/cbpanel/CBpanel/__init__.py", line 73, in load_plugin
    plugwidget = plugin.Plugin(self.panel, settings)
  File "/usr/share/cbpanel/CBpanel/plugins/pager.py", line 25, in __init__
    active_workspace = active_workspace.get_number()
AttributeError: 'NoneType' object has no attribute 'get_number'
[INFO   ] Loading plugin 'separator' ..
[INFO   ] Loading plugin 'windowlist' ..
[INFO   ] Loading plugin 'separator' ..
[INFO   ] Loading plugin 'searchbox' ..
[DEBUG  ] SearchBox: Browser set to 'firefox %s'
[INFO   ] Loading plugin 'terminal' ..
[INFO   ] Loading plugin 'separator' ..
[INFO   ] Loading plugin 'systray' ..
[INFO   ] Loading plugin 'clock' ..
[DEBUG  ] Clock: Clock not displaying seconds: updated scheduled once every minute.
[INFO   ] Loading plugin 'settings' ..

Attached a screenshot

---

### Post by .kkursor on 2009-07-22
It seems that you have no window manager running. Try starting xdm.

---

### Post by durand on 2009-07-22
Have you made sure that your programs in autostart.sh all have a "&" after them? Thats the problem I had.

---

### Post by ~sHyLoCk~ on 2009-07-22
How are you launching openbox?

---

### Post by stepper on 2009-07-22
> **durand said:**
> Have you made sure that your programs in autostart.sh all have a "&" after them? Thats the problem I had.

Thanks, that was the problem my last entry in autostart.sh did not have "&" at the end.

@ ~sHyLoCk~ : Openbox is launched from GDM.

---

### Post by ~sHyLoCk~ on 2009-07-23
> **stepper said:**
> 
@ ~sHyLoCk~ : Openbox is launched from GDM.

You can launch via .xinitrc as well.

---

### Post by durand on 2009-07-23
Whats the advantage of using xinit over a desktop manager such as SLiM? I might just use xinit on its own if it helps..

---

### Post by ~sHyLoCk~ on 2009-07-23
> **durand said:**
> Whats the advantage of using xinit over a desktop manager such as SLiM? I might just use xinit on its own if it helps..

I just love the VC login.

---

