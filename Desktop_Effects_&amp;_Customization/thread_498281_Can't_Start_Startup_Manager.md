---
title: "Can't Start Startup Manager"
date: 2007-07-11
forum: Desktop Effects &amp; Customization
---

### Post by gidra on 2007-07-11
When i run startup manager i'm getting this : 


/var/lib/python-support/python2.5/startupmanager/gtk_frontend.py:710: GtkWarning: Unable to locate theme engine in module_path: "experience",
  'startupmanager.glade'), None ,APP)
/home/eman/.themes/blue carboon/gtk-2.0/gtkrc:65: Unable to locate image file in pixmap_path: "menubg.png"
/home/eman/.themes/blue carboon/gtk-2.0/gtkrc:177: Unable to locate image file in pixmap_path: "Arrows/arrow-up.png"
/home/eman/.themes/blue carboon/gtk-2.0/gtkrc:181: Overlay image options specified without filename
/home/eman/.themes/blue carboon/gtk-2.0/gtkrc:330: Unable to locate image file in pixmap_path: "Combo/combo-arrow-insens.png"
/home/eman/.themes/blue carboon/gtk-2.0/gtkrc:332: Overlay image options specified without filename

** (startupmanager:12947): WARNING **: Invalid borders specified for theme pixmap:
        /home/eman/.themes/blue carboon/gtk-2.0/Lines/line-h.png,
borders don't fit within the image

** (startupmanager:12947): WARNING **: Invalid borders specified for theme pixmap:
        /home/eman/.themes/blue carboon/gtk-2.0/Toolbar/toolbar.png,
borders don't fit within the image

** (startupmanager:12947): WARNING **: Invalid borders specified for theme pixmap:
        /home/eman/.themes/blue carboon/gtk-2.0/Lines/line-v.png,
borders don't fit within the image
Exception in thread Thread-1:
Traceback (most recent call last):
  File "threading.py", line 460, in __bootstrap
    self.run()
  File "/var/lib/python-support/python2.5/startupmanager/gtk_frontend.py", line 150, in run
    self.grub = Grub()
  File "/var/lib/python-support/python2.5/startupmanager/base.py", line 1006, in __init__
    self.__try_backup_config_file()
  File "/var/lib/python-support/python2.5/startupmanager/base.py", line 170, in __try_backup_config_file
    shutil.copy(self.menu, self.menu + ".backup")
  File "shutil.py", line 80, in copy
    copyfile(src, dst)
  File "shutil.py", line 47, in copyfile
    fdst = open(dst, 'wb')
IOError: [Errno 13] Permission denied: '/boot/grub/menu.lst.backup'

Traceback (most recent call last):
  File "/usr/bin/startupmanager", line 26, in <module>
    main()
  File "/usr/bin/startupmanager", line 23, in main
    app = startupmanager.main()
  File "/var/lib/python-support/python2.5/startupmanager/__init__.py", line 4, in main
    SumGui()
  File "/var/lib/python-support/python2.5/startupmanager/gtk_frontend.py", line 732, in __init__
    self.grub = thread.grub
AttributeError: 'StartupThread' object has no attribute 'grub'

Any ideas please?

---

