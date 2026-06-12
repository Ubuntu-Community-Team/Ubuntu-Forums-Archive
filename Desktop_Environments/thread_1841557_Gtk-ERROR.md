---
title: "Gtk-ERROR"
date: 2011-09-09
forum: Desktop Environments
---

### Post by saedz on 2011-09-09
Hello!

I had a partial update on my ubuntu 11.04, the Nautilus doesn't work properly anymore and returns the following error:

Gtk-ERROR **: GTK+ 2.x symbols detected. Using GTK+ 2.x and GTK+ 3 in the same process is not supported
aborting...
Aborted

what am I gonna do now?

cheers

---

### Post by raja.genupula on 2011-09-09
you have installed both gtk 2 and gtk 3 ...you must remove one .
remove gtk 3 . then try again

---

### Post by saedz on 2011-09-10
Hi

I tried to uninstall gtk 3 but it seems it is not installed 

sudo apt-get remove gtk2[tab]
gtk2-engines          gtk2-engines-murrine  gtk2-engines-pixbuf

in the software center I have:
libcanberra-gtk3-0
libdbusmenu-gtk3

Regards

---

### Post by raja.genupula on 2011-09-10
[http://ubuntuforums.org/showthread.php?t=1667057](http://ubuntuforums.org/showthread.php?t=1667057)
 
 
follow this

---

### Post by saedz on 2011-09-10
---------dpkg -l | grep gtk

ii  appmenu-gtk                        0.2.1-0ubuntu3                                                 Export GTK menus over DBus
ii  apport-gtk                            1.20.1-0ubuntu5                                                GTK+ frontend for the apport crash report system
ii  checkbox-gtk                          0.11.3                                                         GTK interface for checkbox
ii  computer-janitor-gtk                  2.1.0-0ubuntu4                                                 Clean up a system so it's more like a freshly installed one
ii  gir1.2-gtk-2.0                        2.24.4-0ubuntu2                                                The GTK+ graphical user interface library -- gir bindings
ii  gir1.2-gtk-3.0                        3.0.12-0ubuntu1~natty1                                         GTK+ graphical user interface library -- gir bindings
ii  gtk2-engines                          1:2.20.2-0ubuntu1                                              theme engines for GTK+ 2.x
ii  gtk2-engines-murrine                  0.98.1.1-0ubuntu3                                              cairo-based gtk+-2.0 theme engine
ii  gtk2-engines-pixbuf                   2.24.4-0ubuntu2                                                Pixbuf-based theme for GTK+ 2.x
ii  ibus-gtk                              1.3.9-2ubuntu1~natty1                                          New input method framework using dbus (GTK+2 support)
ii  jockey-gtk                            0.9.2-0ubuntu5                                                 GNOME user interface and desktop integration for driver management
rc  libavahi-ui-gtk3-0                    0.6.30-3ubuntu1~natty1                                         Avahi GTK+ User interface library for GTK3
ii  libcanberra-gtk-module                0.28-0ubuntu7~natty1                                           translates Gtk+ widgets signals to event sounds
ii  libcanberra-gtk0                      0.28-0ubuntu7~natty1                                           Gtk+ helper for playing widget event sounds with libcanberra
ii  libcanberra-gtk3-0                    0.28-0ubuntu7~natty1                                           Gtk+ 3.0 helper for playing widget event sounds with libcanberra
ii  libclutter-gtk-0.10-0                 0.10.8-1ubuntu1                                                Open GL based interactive canvas library GTK+ widget
rc  libclutter-gtk-1.0-0                  1.0.2-0ubuntu2~natty1                                          Open GL based interactive canvas library GTK+ widget
rc  libdbusmenu-gtk1                      0.3.16-0ubuntu1                                                library for passing menus over DBus - GTK+ version
ii  libdbusmenu-gtk3                      0.4.3-0ubuntu4                                                 library for passing menus over DBus - GTK+ version
rc  libdbusmenu-gtk3-3                    0.4.3-0ubuntu3                                                 library for passing menus over DBus - GTK+ version
ii  libgdu-gtk0                           2.32.1-0ubuntu4                                                GTK+ standard dialog library for libgdu
ii  libgtk-3-0                            3.0.12-0ubuntu1~natty1                                         GTK+ graphical user interface library
ii  libgtk-3-bin                          3.0.12-0ubuntu1~natty1                                         programs for the GTK+ graphical user interface library
ii  libgtk-3-common                       3.0.12-0ubuntu1~natty1                                         common files for the GTK+ graphical user interface library
ii  libgtk-sharp-beans-cil                2.14.1-1                                                       Supplementary CLI bindings for GTK 2.14+
ii  libgtk-vnc-1.0-0                      0.4.3-0ubuntu3                                                 A VNC viewer widget for GTK+ (runtime libraries)
rc  libgtk-vnc-2.0-0                      0.4.3-2ubuntu2~natty1                                          VNC viewer widget for GTK+3 (runtime libraries)
ii  libgtk2-perl                          2:1.223-1                                                      Perl interface to the 2.x series of the Gimp Toolkit library
ii  libgtk2.0-0                           2.24.4-0ubuntu2                                                The GTK+ graphical user interface library
ii  libgtk2.0-bin                         2.24.4-0ubuntu2                                                The programs for the GTK+ graphical user interface library
ii  libgtk2.0-cil                         2.12.10-1ubuntu1                                               CLI binding for the GTK+ toolkit 2.12
ii  libgtk2.0-common                      2.24.4-0ubuntu2                                                Common files for the GTK+ graphical user interface library
rc  libgtkhtml-4.0-0                      4.0.1-2~natty1                                                 HTML rendering/editing library - runtime files
rc  libgtkhtml-editor-4.0-0               4.0.1-2~natty1                                                 HTML rendering/editing library - editor widget
ii  libgtkhtml-editor-common              1:3.32.2-0ubuntu1                                              HTML rendering/editing library - editor widget data
ii  libgtkhtml-editor0                    1:3.32.2-0ubuntu1                                              HTML rendering/editing library - editor widget
ii  libgtkhtml3.14-19                     1:3.32.2-0ubuntu1                                              HTML rendering/editing library - runtime files
ii  libgtkmm-2.4-1c2a                     1:2.24.0-0ubuntu1                                              C++ wrappers for GTK+ (shared libraries)
rc  libgtkmm-3.0-1                        3.0.1-1~natty1                                                 C++ wrappers for GTK+ (shared libraries)
rc  libgtksourceview-3.0-0                3.0.5-0ubuntu1~natty1                                          shared libraries for the GTK+ syntax highlighting widget
ii  libgtksourceview2.0-0                 2.10.5-0ubuntu3                                                shared libraries for the GTK+ syntax highlighting widget
ii  libgtksourceview2.0-common            2.10.5-0ubuntu3                                                common files for the GTK+ syntax highlighting widget
ii  libgtkspell0                          2.0.16-1                                                       a spell-checking addon for GTK's TextView widget
ii  libido-0.1-0                          0.2.2-0ubuntu1                                                 Shared library providing extra gtk menu items for display in
ii  libindicate-gtk2                      0.5.0-0ubuntu2                                                 library for raising indicators via DBus - GTK bindings
ii  libpolkit-gtk-1-0                     0.102-1ubuntu1~natty1                                          PolicyKit GTK+ API
ii  libreoffice-gtk                       1:3.3.3-1ubuntu2                                               office productivity suite -- GTK+ integration
ii  libwebkitgtk-1.0-0                    1.4.3-0ubuntu1~natty1                                          Web content engine library for Gtk+
ii  libwebkitgtk-1.0-common               1.4.3-0ubuntu1~natty1                                          Web content engine library for Gtk+ - data files
rc  libwebkitgtk-3.0-0                    1.4.2-0ubuntu1~natty1                                          Web content engine library for Gtk+
ii  libwmf0.2-7-gtk                       0.2.8.4-7ubuntu3                                               Windows metafile conversion library
ii  libwxgtk2.8-0                         2.8.11.0-0ubuntu8                                              wxWidgets Cross-platform C++ GUI toolkit (GTK+ runtime)
ii  openoffice.org-gtk                    1:3.3.0-7ubuntu2                                               office productivity suite -- GTK+ integration
ii  python-aptdaemon-gtk                  0.41+bzr646-0ubuntu2.1                                         Transitional dummy package
ii  python-aptdaemon.gtk3widgets          0.41+bzr646-0ubuntu2.1                                         Python GTK+ 3 widgets to run an aptdaemon client
ii  python-aptdaemon.gtkwidgets           0.41+bzr646-0ubuntu2.1                                         Python GTK+ 2 widgets to run an aptdaemon client
ii  python-gtk2                           2.22.0-0ubuntu1.1                                              Python bindings for the GTK+ widget set
ii  python-gtksourceview2                 2.10.1-1build1                                                 Python bindings for the GtkSourceView widget
ii  python-gtkspell                       2.25.3-7ubuntu2                                                Python bindings for the GtkSpell library
ii  software-properties-gtk               0.80.9                                                         manage the repositories that you install software from
ii  transmission-gtk                      2.13-0ubuntu8                                                  lightweight BitTorrent client (GTK interface)
ii  ubuntuone-control-panel-gtk           1.0.0-0ubuntu1.1                                               Ubuntu One Control Panel
ii  usb-creator-gtk                       0.2.28.3                                                       create a startup disk using a CD or disc image (for GNOME)
ii  xdg-user-dirs-gtk                     0.8-1ubuntu1                                                   tool to manage well known user directories (Gtk extension)


----------------Results:

sudo apt-get purge libgtk3.0-0 2.99.2-1

[sudo] password for user
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'libgtk3.0-0' can't be removed
E: Unable to locate package 2.99.2-1
E: Couldn't find any package by regex '2.99.2-1'

user@user-PC:~$ sudo apt-get purge libgtk3.0-0

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'libgtk3.0-0' can't be removed
The following packages were automatically installed and are no longer required:
  libseed0 gir1.2-gstreamer-0.10 gir1.2-json-glib-1.0 gir1.2-clutter-1.0
  gnome-js-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 80 not upgraded.

user@user-PC:~$ sudo apt-get autoremove libgtk3.0-0

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'libgtk3.0-0' can't be removed
The following packages will be REMOVED:
  gir1.2-clutter-1.0 gir1.2-gstreamer-0.10 gir1.2-json-glib-1.0
  gnome-js-common libseed0
0 upgraded, 0 newly installed, 5 to remove and 79 not upgraded.
After this operation, 1,798 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 206755 files and directories currently installed.)
Removing libseed0 ...
Removing gir1.2-clutter-1.0 ...
Removing gir1.2-gstreamer-0.10 ...
Removing gir1.2-json-glib-1.0 ...
Removing gnome-js-common ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place



What should I do now? do I need to restart?

---

### Post by raja.genupula on 2011-09-10
use nautilus now 
if its not done then try again by restarting your system

---

### Post by saedz on 2011-09-10
I used nautilus, then restarted, but unfortunately, I am receiving the same error when opening nautilus :(

---

### Post by saedz on 2011-09-10
I used nautilus and restarted, but unfortunately nothing is changed

---

### Post by raja.genupula on 2011-09-10
hey man , sorry for not getting this . could you please do this .
try to re-install nautilus
or
remove gnome 3 completely .

---

### Post by saedz on 2011-09-10
alright dude

by the way many thanks for your kind help
should I close the thread?

cheers

---

### Post by raja.genupula on 2011-09-10
give me some time , this issue looking complex to me . dont close it as solved because it not solved . here many experts are there , any one can look at this & gonna help you .

---

### Post by raja.genupula on 2011-09-10
yeah i have seen your PM . i am glad that you have solved this issue . now you can mark it as solved . 

regards

---

