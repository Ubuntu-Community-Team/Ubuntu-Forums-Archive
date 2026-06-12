---
title: "Gnome Shell"
date: 2010-02-10
forum: Desktop Environments
---

### Post by yester64 on 2010-02-10
Hi,

i installed gnomeshell from the repositories and i notice that once i try to change settings, i am getting errors.
Is there anything you have to install to it, or is it just a bug?

> joerg@joerg-desktop:~$ gnome-shell --replace
      JS LOG: conforming method: IntrospectRemote for org.freedesktop.DBus.Introspectable
      JS LOG: Loading tweener.js
      JS LOG: Loading tweenlist.js
      JS LOG: Done loading tweenlist.js
      JS LOG: Done loading tweener.js
      JS LOG: Loading equations.js
      JS LOG: Done loading equations.js

(nautilus:23884): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Window manager warning: Log level 8: meta_window_set_user_time: assertion `!window->override_redirect' failed
Window manager warning: Log level 8: meta_window_raise: assertion `!window->override_redirect' failed
Window manager warning: Log level 8: meta_window_focus: assertion `!window->override_redirect' failed

** (gnome-control-center:25303): WARNING **: 
error raised: [libslab_get_gconf_value: error getting /desktop/gnome/applications/main-menu/lock-down/user_modifiable_apps]


** (gnome-control-center:25303): WARNING **: 


---

