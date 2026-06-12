---
title: "AWN: White Lines - Python Libraries Corrupted?"
date: 2008-01-02
forum: Desktop Effects &amp; Customization
---

### Post by xItachi on 2008-01-02
Hi, I've been using AWN for about 2 days now, and I haven't had a problem with it since, except now.  I see two white lines for what should be the Show Desktop and the Quit/Logout applet.  Below is the output I received from running avant-window-navigator in the terminal:
```

Screen is composited.
APPLET : /usr/lib/awn/applets/showdesktop.desktop
Traceback (most recent call last):
  File "/usr/lib/awn/applets/showdesktop/showdesktop.py", line 32, in <module>
    import pygtk
ImportError: No module named pygtk
LOADED : /home/stephen/.config/awn/launchers/awn_launcher.desktop
LOADED : /home/stephen/.config/awn/launchers/awn_launcher-1.desktop
LOADED : /home/stephen/.config/awn/launchers/awn_launcher-2.desktop
LOADED : /home/stephen/.config/awn/launchers/awn_launcher-3.desktop
LOADED : /home/stephen/.config/awn/launchers/awn_launcher-4.desktop
APPLET : /usr/lib/awn/applets/taskman.desktop
APPLET : /usr/lib/awn/applets/quit-applet.desktop
Traceback (most recent call last):
  File "/usr/lib/awn/applets/quit-applet/quit-applet.py", line 21, in <module>
    import gobject
ImportError: No module named gobject

```

It says I'm missing a module called pygtk and gobject.  I have reason to believe that my Python is corrupted because before I last restarted my computer, I was trying to install an application and it didn't compile correctly so I was trying to reinstall my Python.  I was playing around a bit with Python and now it has come to this.  I did an install of the latest version of Python and I still have this problem.  I've checked other threads and other people were just missing some dependencies, but I don't think that is the problem for me, because my Screenlets/Desklets are not working as well (and I think those are written in Python).  If anyone can help that would be nice, thank you.

---

