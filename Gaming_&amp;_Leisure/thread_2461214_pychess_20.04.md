---
title: "pychess 20.04"
date: 2021-04-26
forum: Gaming &amp; Leisure
---

### Post by cmcanulty on 2021-04-26
Has anyone gotten pychess to open in 20.04? I installed it and the dependencies listed here:

[https://launchpad.net/ubuntu/focal/+source/pychess]("https://launchpad.net/ubuntu/focal/+source/pychess")

won't open I also tried removing and reinstalling and opening from terminal.  Nothing, not even an error message

---

### Post by spjackson on 2021-04-30
Yes, I have a working pychess on 20.04 after doing:
```

sudo apt install pychess

```

---

### Post by cmcanulty on 2021-04-30
I tried that first of course. it is installed but won't run. Below is the error message. Thank you

```
cmcanulty@Dell660s:~$ sudo apt install pychess
[sudo] password for cmcanulty: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pychess is already the newest version (0.12.2-1build1).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
cmcanulty@Dell660s:~$ pychess

(pychess:32052): Gtk-WARNING **: 07:31:57.312: Theme parsing error: gtk.css:27:35: Junk at end of value for background-color

(pychess:32052): Gtk-WARNING **: 07:31:57.312: Theme parsing error: gtk.css:40:48: Junk at end of value for background-color

(pychess:32052): Gtk-WARNING **: 07:31:57.312: Theme parsing error: gtk.css:48:46: Junk at end of value for background-color

(pychess:32052): Gtk-WARNING **: 07:31:57.312: Theme parsing error: gtk.css:59:58: Junk at end of value for background-color

(pychess:32052): Gtk-WARNING **: 07:31:57.312: Theme parsing error: gtk.css:66:28: The :prelight pseudo-class is deprecated. Use :hover instead.

(pychess:32052): Gtk-WARNING **: 07:31:57.312: Theme parsing error: gtk.css:70:46: Junk at end of value for background-color

(pychess:32052): Gtk-WARNING **: 07:31:57.312: Theme parsing error: gtk.css:77:35: The :prelight pseudo-class is deprecated. Use :hover instead.

(pychess:32052): Gtk-WARNING **: 07:31:57.312: Theme parsing error: gtk.css:81:58: Junk at end of value for background-color

(pychess:32052): Gtk-WARNING **: 07:31:57.313: Theme parsing error: gtk.css:123:31: The :insensitive pseudo-class is deprecated. Use :disabled instead.

(pychess:32052): Gtk-WARNING **: 07:31:57.313: Theme parsing error: gtk.css:124:24: The :insensitive pseudo-class is deprecated. Use :disabled instead.

(pychess:32052): Gtk-WARNING **: 07:31:57.313: Theme parsing error: gtk.css:156:27: The :insensitive pseudo-class is deprecated. Use :disabled instead.

(pychess:32052): Gtk-WARNING **: 07:31:57.313: Theme parsing error: gtk.css:157:29: The :insensitive pseudo-class is deprecated. Use :disabled instead.

(pychess:32052): Gtk-WARNING **: 07:31:57.313: Theme parsing error: gtk.css:177:34: The :insensitive pseudo-class is deprecated. Use :disabled instead.

(pychess:32052): Gtk-WARNING **: 07:31:57.313: Theme parsing error: gtk.css:199:34: The :inconsistent pseudo-class is deprecated. Use :indeterminate instead.
/usr/lib/python2.7/dist-packages/pychess/System/gstreamer.py:35: PyGIWarning: Gst was imported without specifying a version first. Use gi.require_version('Gst', '1.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gst
Traceback (most recent call last):
  File "/usr/games/pychess", line 179, in <module>
    purge_recent, chess_file, ics_host, ics_port)
  File "/usr/lib/python2.7/dist-packages/pychess/Main.py", line 521, in run
    pychess = PyChess(log_viewer, chess_file)
  File "/usr/lib/python2.7/dist-packages/pychess/Main.py", line 329, in __init__
    self.initGlade(log_viewer)
  File "/usr/lib/python2.7/dist-packages/pychess/Main.py", line 341, in initGlade
    new_game_tasker, internet_game_tasker = NewGameTasker(), InternetGameTasker()
  File "/usr/lib/python2.7/dist-packages/pychess/widgets/TaskerManager.py", line 265, in __init__
    uistuff.keep(self.widgets["passwordEntry"], "passwordEntry")
  File "/usr/lib/python2.7/dist-packages/pychess/System/uistuff.py", line 194, in keep
    setFromConf()
  File "/usr/lib/python2.7/dist-packages/pychess/System/uistuff.py", line 185, in setFromConf
    set_value(v)
TypeError: Must be string, not int
cmcanulty@Dell660s:~$ ^C
cmcanulty@Dell660s:~$ 
```

---

### Post by spjackson on 2021-04-30
When I run it from the terminal, the only warning I get at startup is
```

/usr/lib/python2.7/dist-packages/pychess/System/gstreamer.py:35: PyGIWarning: Gst was imported without specifying a version first. Use gi.require_version('Gst', '1.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gst

```
(There are further warnings during play.) Your fatal error is
```
  File "/usr/lib/python2.7/dist-packages/pychess/System/uistuff.py", line 185, in setFromConf     set_value(v)
TypeError: Must be string, not int

```
I am running on Ubuntu Studio which is Xfce based. It looks to me like one of your Gnome or theme settings isn't compatible with pychess, but I don't know what.

---

### Post by Frogs Hair on 2021-04-30
I saw a similar gtk warning , but the application  did install and then I had to update it. There is a .deb for the latest version the linked page but, I can't be sure it will make any difference.The application itself linked the update page.
[https://github.com/pychess/pychess/releases](https://github.com/pychess/pychess/releases)

```
dpkg-preconfigure:4192): Gtk-WARNING **: 08:50:45.046: Theme parsing error: gtk.css:4188:4: Junk at end of value for min-height

(dpkg-preconfigure:4189): Gtk-WARNING **: 08:50:45.178: Theme parsing error: gtk.css:4188:4: Junk at end of value for min-height
Selecting previously unselected package libgtksourceview-3.0-common.
(Reading database ... 342743 files and directories currently installed.)
Preparing to unpack .../00-libgtksourceview-3.0-common_3.24.11-2_all.deb ...
Unpacking libgtksourceview-3.0-common (3.24.11-2) ...
Selecting previously unselected package libgtksourceview-3.0-1:amd64.
Preparing to unpack .../01-libgtksourceview-3.0-1_3.24.11-2_amd64.deb ...
Unpacking libgtksourceview-3.0-1:amd64 (3.24.11-2) ...
Selecting previously unselected package gir1.2-gtksource-3.0:amd64.
Preparing to unpack .../02-gir1.2-gtksource-3.0_3.24.11-2_amd64.deb ...
Unpacking gir1.2-gtksource-3.0:amd64 (3.24.11-2) ...
Selecting previously unselected package gir1.2-rsvg-2.0:amd64.
Preparing to unpack .../03-gir1.2-rsvg-2.0_2.50.3+dfsg-1_amd64.deb ...
Unpacking gir1.2-rsvg-2.0:amd64 (2.50.3+dfsg-1) ...
Selecting previously unselected package python3-distutils.
Preparing to unpack .../04-python3-distutils_3.9.4-0ubuntu1_all.deb ...
Unpacking python3-distutils (3.9.4-0ubuntu1) ...
Selecting previously unselected package python3-markdown.
Preparing to unpack .../05-python3-markdown_3.3.4-1_all.deb ...
Unpacking python3-markdown (3.3.4-1) ...
Selecting previously unselected package gobject-introspection.
Preparing to unpack .../06-gobject-introspection_1.66.1-1build1_amd64.deb ...
Unpacking gobject-introspection (1.66.1-1build1) ...
Selecting previously unselected package python3-websockets.
Preparing to unpack .../07-python3-websockets_8.1-1_all.deb ...
Unpacking python3-websockets (8.1-1) ...
Selecting previously unselected package libgaviotatb1.
Preparing to unpack .../08-libgaviotatb1_0.4-2.1_amd64.deb ...
Unpacking libgaviotatb1 (0.4-2.1) ...
Selecting previously unselected package gaviotatb.
Preparing to unpack .../09-gaviotatb_0.4-2.1_all.deb ...
Unpacking gaviotatb (0.4-2.1) ...
Selecting previously unselected package pychess.
Preparing to unpack .../10-pychess_1.0.0-1.1_all.deb ...
Unpacking pychess (1.0.0-1.1) ...
Selecting previously unselected package python3-pygments.
Preparing to unpack .../11-python3-pygments_2.7.1+dfsg-2ubuntu1_all.deb ...
Unpacking python3-pygments (2.7.1+dfsg-2ubuntu1) ...
Setting up python3-distutils (3.9.4-0ubuntu1) ...
Setting up python3-pygments (2.7.1+dfsg-2ubuntu1) ...
Setting up python3-markdown (3.3.4-1) ...
Setting up libgaviotatb1 (0.4-2.1) ...
Setting up libgtksourceview-3.0-common (3.24.11-2) ...
Setting up gir1.2-rsvg-2.0:amd64 (2.50.3+dfsg-1) ...
Setting up gaviotatb (0.4-2.1) ...
Setting up python3-websockets (8.1-1) ...
Setting up gobject-introspection (1.66.1-1build1) ...
Setting up libgtksourceview-3.0-1:amd64 (3.24.11-2) ...
Setting up gir1.2-gtksource-3.0:amd64 (3.24.11-2) ...
Setting up pychess (1.0.0-1.1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu1) ...
Processing triggers for libc-bin (2.33-0ubuntu5) ...
Processing triggers for man-db (2.9.4-2) ...
Processing triggers for shared-mime-info (2.0-1) ...

```

---

### Post by cmcanulty on 2021-04-30
OK good the github installed and opens but I am getting a popup box requiring various permissions but not sure if I have to install these as they aren't on the github link or somehow change permission for something

[ATTACH=CONFIG]288396[/ATTACH]

---

### Post by cmcanulty on 2021-04-30
I finally got it after purging pychess and then removing many files still there for pychess by the locate command I finally got it flushed out the many files that remained and then reinstalled deb from your link. I still get the startup errors but it works. Suggestion to someone in Ubuntu is to replace the repository version with the github that actually opens and works. Thanks all

---

### Post by sergi009 on 2021-10-01
hiii

---

