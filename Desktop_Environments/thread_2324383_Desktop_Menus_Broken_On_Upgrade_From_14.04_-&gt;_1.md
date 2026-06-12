---
title: "Desktop Menus Broken On Upgrade From 14.04 -&gt; 16.04"
date: 2016-05-13
forum: Desktop Environments
---

### Post by CharlesT423 on 2016-05-13
Hello,

  I upgraded my desktop running Ubuntu + LXDE (Lubuntu session) tonight and it seems to have broken my menus.  The menu button is empty (other than the Logout and Run entries) and if I try to add a launcher button to the panel it fails to generate an application list.  I also tried running Alacarte to edit the menus but get the following error:

> /usr/share/alacarte/Alacarte/MainWindow.py:22: PyGIWarning: GMenu was imported without specifying a version first. Use gi.require_version('GMenu', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk, GdkPixbuf, Gdk, GMenu

(alacarte:18061): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion 'gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(alacarte:18061): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion 'gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 26, in <module>
    main()
  File "/usr/share/alacarte/Alacarte/MainWindow.py", line 464, in main
    app.setMenuBasename(basename)
  File "/usr/share/alacarte/Alacarte/MainWindow.py", line 62, in setMenuBasename
    self.editor = MenuEditor(menu_basename)
  File "/usr/share/alacarte/Alacarte/MenuEditor.py", line 36, in __init__
    self.load()
  File "/usr/share/alacarte/Alacarte/MenuEditor.py", line 49, in load
    if not self.tree.load_sync():
GLib.Error: g-io-error-quark: Failed to look up menu_file for "lapplications.menu"
 (0)


If I login with a test user things seem to work fine, so it seems to just be a problem with something in my user settings.  Does anyone know how to diagnose this other than "delete .local and .config and start from scratch"?

---

### Post by CharlesT423 on 2016-05-14
Just replying to myself in case anyone else runs into this issue.  The problem seems to be that the desktop menus changed from the l- prefix to lxde-.  To fix it edit ~/.config/lxsession/Lubuntu/desktop.conf and change menu_prefix=l- to menu_prefix=lxde- in the [Environment] block.

---

