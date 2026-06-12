---
title: "Automatix2 on Dapper, wierd crash"
date: 2006-11-10
forum: Desktop Environments
---

### Post by shane2peru on 2006-11-10
Ok, I installed Automatix2 because Automatix was not installing the Firefox plugins, it kept failing to download the files.  Now, when I run Automatix2 Click through the directories, and it updates the sources, then it just disappears.  No error message, no warning, just disappears.  I ran it in a Terminal to see the problem, and it is beyond my, here is the problem, ```

-laptop:~$ automatix2
Traceback (most recent call last):
  File "/usr/bin/automatix.py", line 37, in ?
    main = start_main()
  File "/usr/lib/automatix2/main_interface.py", line 95, in __init__
    self.build_interface()
  File "/usr/lib/automatix2/main_interface.py", line 111, in build_interface
    self.generate_menus()
  File "/usr/lib/automatix2/main_interface.py", line 122, in generate_menus
    self.generate_catalog_model()
  File "/usr/lib/automatix2/main_interface.py", line 374, in generate_catalog_model
    icon= gtk.gdk.pixbuf_new_from_file(list.icon)
gobject.GError: Failed to open file '/usr/share/icons/Tango/24x24/devices/drive-cdrom.png': No such file or directory

```Any ideas?  This is really annoying.  Oh, I'm using Dapper - Christian Edition.

Shane

---

### Post by arnieboy on 2006-11-10
do the following:
```
sudo apt-get install tango-icon-theme
```
and run automatix2 again.

---

### Post by shane2peru on 2006-11-12
anrieboy,  

   Thanks for the reply.  I gave that a try and here is the results: ```

 sudo apt-get install tango-icon-theme
Password:
Reading package lists... Done
Building dependency tree... Done
tango-icon-theme is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
shane@shane-laptop:~$ automatix2
Starting
Traceback (most recent call last):
  File "/usr/bin/automatix.py", line 68, in ?
    main = main_ui()
  File "/media/hda11/home/arnav/resin2/debtree/source/usr/lib/automatix2/main_interface.py", line 12, in __init__
  File "/media/hda11/home/arnav/resin2/debtree/source/usr/lib/automatix2/main_interface.py", line 50, in build_interface
  File "/media/hda11/home/arnav/resin2/debtree/source/usr/lib/automatix2/main_interface.py", line 92, in generate_menus
  File "/media/hda11/home/arnav/resin2/debtree/source/usr/lib/automatix2/main_interface.py", line 349, in generate_catalog_model
gobject.GError: Failed to open file '/usr/share/icons/Tango/24x24/devices/drive-cdrom.png': No such file or directory

```

I also noticed that there was an update today and it was Automatix2,  I thought that maybe that may fix it.  I guess back to the drawing board.  I don't think I have any wierd installations on my computer.  I installed a clean install of Christian Ubuntu after my installation of Edgy had too many problems.  I wiped everything and started fresh.  Any more ideas?

Shane

---

