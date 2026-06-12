---
title: "Caja v1.26.0-1ubuntu1 frequent crashing on UbuntuMATE 22.04"
date: 2023-06-18
forum: Desktop Environments
---

### Post by watchpocket on 2023-06-18
Caja crashes when I open any folder containing JPGs or PDFs.  The folder instantly disappears. after a second or two.

 Here is a sample of the warnings that .xsession-errors is showing:

```

368 (caja:8266): Gtk-CRITICAL **: 14:10:37.407: gtk_container_foreach: assertion 'GTK_IS_CONTAINER (container)' failed
369
370 (mate-panel:2265): Gtk-CRITICAL **: 14:12:42.312: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed371 RuntimeError: object at 0x7fd86c97dbc0 of type FolderColorMenu is not initialized
372 RuntimeError: object at 0x7fd86c97dbc0 of type FolderColorMenu is not initialized
373  
374 ** (caja:8266): CRITICAL **: 14:29:25.024: caja_bookmark_get_location: assertion 'CAJA_IS_BOOKMARK (bookmark)' failed
375  
376 (caja:8266): GLib-GIO-CRITICAL **: 14:29:25.024: g_file_get_uri: assertion 'G_IS_FILE (file)' failed
377 sys:1: Warning: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
378 RuntimeError: object at 0x7fd86c97dbc0 of type FolderColorMenu is not initialized

406 (caja:8659): Gtk-WARNING **: 14:29:38.150: Failed to register client: GDBus.Error:org.gnome.SessionManager.AlreadyRegistered: Unable to register client
```

Any suggestions appreciated.

---

