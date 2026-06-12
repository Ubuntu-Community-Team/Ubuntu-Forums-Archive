---
title: "Self Executing Screenlet Daemon?"
date: 2008-03-09
forum: Desktop Effects &amp; Customization
---

### Post by rotaryfan on 2008-03-09
Hey, I'm a bit new to compiz and screenlets, but up until I added new screenlets to the daemon everything was fine.  upon adding half a dozen screenlets using the installer, the daemon self executes infinitely if I open it once.  I also cannot open any screenlets using the right click function.  is this a malfunctioning screenlet, or is there a known fix for this?  is this a common problem? any and all help is appreciated.

---

### Post by Akedz on 2008-03-10
i have a bit of a problem too with screenlets manager. i have a fresh install, have ccsm and all those. the problem is the manager won't open. i tried running as root, it opens but i can't add screenlets. also try running it normally through terminal and this is what i get:

> 
It looks like you are running gnome
/usr/share/screenlets-manager/screenlets-manager.py:253: Warning: Two different plugins tried to register 'RsvgHandle'.
  self.tips = gtk.Tooltips()
/usr/share/screenlets-manager/screenlets-manager.py:583: Warning: cannot register existing type `RsvgHandle'
  w.set_icon_from_file('/usr/share/icons/screenlets.svg')
/usr/share/screenlets-manager/screenlets-manager.py:583: Warning: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed
  w.set_icon_from_file('/usr/share/icons/screenlets.svg')
Traceback (most recent call last):
  File "/usr/share/screenlets-manager/screenlets-manager.py", line 1198, in <module>
    app = ScreenletsManager()
  File "/usr/share/screenlets-manager/screenlets-manager.py", line 255, in __init__
    self.create_ui()
  File "/usr/share/screenlets-manager/screenlets-manager.py", line 583, in create_ui
    w.set_icon_from_file('/usr/share/icons/screenlets.svg')
gobject.GError: Failed to load image '/usr/share/icons/screenlets.svg': Error displaying image

---

