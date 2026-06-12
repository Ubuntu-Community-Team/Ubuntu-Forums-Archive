---
title: "Unable to launch cinnamon settings"
date: 2017-11-06
forum: Desktop Environments
---

### Post by marmaladejackson on 2017-11-06
Hi all,

Just upgraded to 17.10 and had to install cinnamon.  I am unable to right-click the desktop or launch the settings dialog by right-clicking the task bar.  If I try to launch the settings manager from the command line I get this:

```
Traceback (most recent call last):
  File "/usr/share/cinnamon/cinnamon-settings/cinnamon-settings.py", line 610, in <module>
    window = MainWindow()
  File "/usr/share/cinnamon/cinnamon-settings/cinnamon-settings.py", line 188, in __init__
    self.window = XApp.GtkWindow(visible=True, window_position=Gtk.WindowPosition.CENTER,
  File "/usr/lib/python2.7/dist-packages/gi/module.py", line 139, in __getattr__
    self.__name__, name))
AttributeError: 'gi.repository.XApp' object has no attribute 'GtkWindow'

```

I think I am missing a library, but I am not sure which one or how to install. Any ideas?

Thanks,
Brian

Edit 1: After playing for a bit, it seems that a lot of things fail while trying to create a window.  Nemo, for example.
```
nemo: symbol lookup error: nemo: undefined symbol: xapp_gtk_window_set_icon_name
```

---

### Post by eljefe6 on 2017-11-19
I had the same problem. If you do an update, only cinnamon is removed and then reinstalled. The other packages don't get updated. I had to do another ```
sudo apt-get dist-upgrade
```

---

### Post by marmaladejackson on 2017-11-19
That did it!

Thanks!

---

