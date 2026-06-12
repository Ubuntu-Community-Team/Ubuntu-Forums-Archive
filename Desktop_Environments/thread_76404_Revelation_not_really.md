---
title: "Revelation: not really"
date: 2005-10-15
forum: Desktop Environments
---

### Post by AlterEgo on 2005-10-15
Installed Revelation (the password manager) 0.4.3-2.
However, when I try and start it
```

revelation

(revelation:8585): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
/usr/lib/python2.4/site-packages/gtk-2.0/gnome/vfs.py:4: DeprecationWarning: Module gnome.vfs is deprecated; please import gnomevfs instead
  DeprecationWarning)
/usr/bin/revelation:42: GtkWarning: locale not supported by C library
  gnome.libgnome_module_info_get(), sys.argv, []
Traceback (most recent call last):
  File "/usr/bin/revelation", line 1359, in ?
    app = Revelation()
  File "/usr/bin/revelation", line 51, in __init__
    self.__init_facilities()
  File "/usr/bin/revelation", line 77, in __init_facilities
    self.items          = ui.ItemFactory(self)
  File "/usr/lib/python2.4/site-packages/revelation/ui.py", line 1168, in __init__
    self.__init_entryicons()
  File "/usr/lib/python2.4/site-packages/revelation/ui.py", line 1199, in __init_entryicons
    self.load_stock_icon(id, name, ( gtk.ICON_SIZE_MENU, ICON_SIZE_DATAVIEW, ICON_SIZE_DROPDOWN, ICON_SIZE_TREEVIEW ))
  File "/usr/lib/python2.4/site-packages/revelation/ui.py", line 1274, in load_stock_icon
    pixbuf = self.theme.load_icon(icon, pixelsize, 0)
GError: Icon 'revelation-fallback-folder' not present in theme

```
Anf that's the end of it.
Anyone have a suggestion how to proceed? Thanks.

---

### Post by AlterEgo on 2005-10-22
I just did a clean breezy kubuntu install,
and now the error message is slightly different, but still revelation is not working:
```

revelation
/usr/lib/python2.4/site-packages/gtk-2.0/gnome/vfs.py:4: DeprecationWarning: Module gnome.vfs is deprecated; please import gnomevfs instead
  DeprecationWarning)
Traceback (most recent call last):
  File "/usr/bin/revelation", line 1359, in ?
    app = Revelation()
  File "/usr/bin/revelation", line 51, in __init__
    self.__init_facilities()
  File "/usr/bin/revelation", line 77, in __init_facilities
    self.items          = ui.ItemFactory(self)
  File "/usr/lib/python2.4/site-packages/revelation/ui.py", line 1168, in __init__
    self.__init_entryicons()
  File "/usr/lib/python2.4/site-packages/revelation/ui.py", line 1199, in __init_entryicons
    self.load_stock_icon(id, name, ( gtk.ICON_SIZE_MENU, ICON_SIZE_DATAVIEW, ICON_SIZE_DROPDOWN, ICON_SIZE_TREEVIEW ))
  File "/usr/lib/python2.4/site-packages/revelation/ui.py", line 1274, in load_stock_icon
    pixbuf = self.theme.load_icon(icon, pixelsize, 0)
GError: Icon 'revelation-fallback-folder' not present in theme

```

I need help :confused:

---

### Post by RYX on 2005-10-22
Hello AlterEgo,

I just came across your message - I'm no Python expert at all, but the error messages seem to be related to an error inside your current theme (although I can't really  say if it means your GNOME-theme ...)  - the script is not able to find the 'revelation-fallback-folder' ... the warning about the deprecated import statement seems to be solved inside vfs.py (it imports gnomevfs after complaining about the deprecated import).

Maybe it helps, if you use the default Ubuntu Theme for your desktop. Alternatively you could try to find out which Python version Revelation is intended to use (maybe 2.4 is too new?) ...

Hope that helps a little bit ...

EDIT: I had another look at the error message... It seems to be missing a single icon inside your theme (Icon 'revelation-fallback-folder' not present in theme) so maybe you can just create a new icon inside your current theme with that name - that could solve the problem.

---

### Post by AlterEgo on 2005-10-22
Thanks for that, RYX,
but changing themes, and adding the file
revelation-fallback-folder.svg to all themes made no difference.

I found a version 0.4.5 on Freshmeat, and I wil try to get it compiled.

---

