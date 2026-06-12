---
title: "problem with awn stacks"
date: 2007-12-05
forum: Desktop Effects &amp; Customization
---

### Post by guko1111 on 2007-12-05
My stacks applet is showing up as a white line, but all the other applets I'm using are loading fine. I have not been able to find a solution to fix this problem after a lot of searching on the forums here. From my research I've gathered that a lot of times this can come down to a missing dependancy. I think that have all the latest installed for awn. Here is the code I get when I run it from the terminal
[PHP]
LOADED : /home/stephen/.config/awn/launchers/awn_launcher-1.desktop
LOADED : /usr/share/applications/gnome-terminal.desktop
LOADED : /usr/share/applications/firefox.desktop
APPLET : /usr/local/lib/awn/applets/taskman.desktop
APPLET : /usr/local/lib/awn/applets/main-menu.desktop
APPLET : /usr/local/lib/awn/applets/quit-applet.desktop
APPLET : /usr/local/lib/awn/applets/stacks.desktop
APPLET : /usr/local/lib/awn/applets/trasher.desktop
APPLET : /usr/local/lib/awn/applets/awnnotificationdaemon.desktop
/usr/local/lib/awn/applets/quit-applet/quit-applet.py:72: Warning: g_object_get_qdata: assertion `G_IS_OBJECT (object)' failed
  applet = App (awn.uid, awn.orient, awn.height)
/usr/local/lib/awn/applets/quit-applet/quit-applet.py:72: Warning: g_object_set_qdata_full: assertion `G_IS_OBJECT (object)' failed
  applet = App (awn.uid, awn.orient, awn.height)
/usr/local/lib/awn/applets/quit-applet/quit-applet.py:72: Warning: g_object_unref: assertion `G_IS_OBJECT (object)' failed
  applet = App (awn.uid, awn.orient, awn.height)

(awn-applet-activation:6181): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

(awn-applet-activation:6181): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed
Traceback (most recent call last):
  File "/usr/local/lib/awn/applets/stacks/stacks.py", line 647, in <module>
    applet = Stacks (awn.uid, awn.orient, awn.height)
  File "/usr/local/lib/awn/applets/stacks/stacks.py", line 116, in __init__
    self.backend_get_config()
  File "/usr/local/lib/awn/applets/stacks/stacks.py", line 634, in backend_get_config
    self.config_backend, self.config_icon_size)
  File "/usr/local/lib/awn/applets/stacks/stacksbackend.py", line 285, in __init__
    Backend.__init__(self, applet, uri, icon_size)
  File "/usr/local/lib/awn/applets/stacks/stacksbackend.py", line 84, in __init__
    self._create_or_open()
  File "/usr/local/lib/awn/applets/stacks/stacksbackend.py", line 292, in _create_or_open
    self.handle = gnomevfs.Handle(self.backend_uri.as_uri(), mode)
gnomevfs.IsDirectoryError: Is a directory
/usr/local/lib/awn/applets/stacks/stacks.py:545: Warning: g_object_get_qdata: assertion `G_IS_OBJECT (object)' failed
  self.applet_set_empty_icon()
/usr/local/lib/awn/applets/stacks/stacks.py:545: Warning: g_object_set_qdata_full: assertion `G_IS_OBJECT (object)' failed
  self.applet_set_empty_icon()
/usr/local/lib/awn/applets/stacks/stacks.py:545: Warning: g_object_unref: assertion `G_IS_OBJECT (object)' failed
  self.applet_set_empty_icon()




[/PHP]

Any help would be appreciated, thanks.

---

