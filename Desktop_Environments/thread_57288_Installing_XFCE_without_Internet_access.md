---
title: "Installing XFCE without Internet access?"
date: 2005-08-15
forum: Desktop Environments
---

### Post by geekdreams on 2005-08-15
Can anyone tell me what files are needed, exactly, to install XFCE on a server configuration of Ubuntu? Since I don't have Internet access on that system, I need to burn everything to a CD and install from there...

---

### Post by jasmuz on 2005-08-15
These are the components of XFCE:

libxfce4util
Library with non-graphical helper functions.

libxfcegui4
Widget library and X Window System interaction.

libxfce4mcs
Settings management library used by most Xfce 4 modules. 

xfce-mcs-manager
Settings manager. Runs in the background and provides global settings information to other Xfce components. There is a main control panel to access the configuration dialogs of Xfce components. 

xfce-mcs-plugins
Settings manager plugins. These plugins provide settings dialogs for general items that are not part of a package, e.g. user interface settings (Gtk+ theme, icon theme, font settings), mouse settings, keyboard settings and display settings. 

xfce4-session
Session manager. The session manager controls the startup and shutdown of the Xfce Desktop Environment. On logout it can save the state of running applications (if the application supports it) and restore them properly again the next time you log in. 

xfwm4
The Xfce 4 window mananger. Manages the placement of application windows on the screen, provides window decorations and manages workspaces. 

xfce4-panel
 The Xfce 4 panel. Provides program lauchers, a workspace switcher, a clock, menus and more. 

xfdesktop
Desktop background manager. This program sets the background image and/or color, and provides a root window menu, a menu panel plugin and a menu editor. 

xfce-utils
Essential utilities and scripts. Provides a taskbar, the Xfce 4 about dialog, a run dialog, the startxfce4 script and several other important scripts. Also contains this user guide. 

xffm
A fast file manager, with double pane and integrated samba network browser. 

xfprint
Printing support. Provides a graphical frontend for printing. Includes xfprint4 and 
xfprint-manager
. 
xfce4-appfinder
An application finder, which allows you to search, launch and find information about applications installed on your system. 

xfcalendar
Simple calendar application with reminders.

gtk-xfce-engine-2
Theme engine for GTK2. Not required for the desktop, but it's a nice theme engine so you might just as well give it a try. 

xfce4-icon-theme
Default icon theme for Xfce 4, called Rodent.

xfwm4-themes
Window decoration themes for xfwm4.

---

### Post by geekdreams on 2005-08-16
Do I just download the .deb files from [http://packages.ubuntu.com](http://packages.ubuntu.com) or are there other files to download as well? (In other words,  I need to know what apt-get does when you issue a command like "apt-get install xfce4".) Thanks!

---

### Post by geekdreams on 2005-08-16
???

---

### Post by jasmuz on 2005-08-16
Yes, pull all the packages i listed from the Ubuntu server, and place them in /var/cache/apt/archives thus making apt that those packages have been pulled from the net, if you encounter a missing dependency just download it and place it too.

---

### Post by geekdreams on 2005-08-17
I downloaded the .deb files and burned them to a CD, added it to sources.list with "apt-cdrom add", and then tried "apt-get install xfce4" but it gives me an error: "Couldn't find package xfce4".

I copied everything from the CD into /var/cache/apt/archives and tried again. Still no luck. The actual file is named xfce4_4.2.1.1_2ubuntu2_all.deb, so I tried "apt-get install xfce4_4.2.1.1_2ubuntu2_all" but that didn't do anything, either. I get the same error each time.

Can/should I add the archives directory to sources.list? Thanks for your help, BTW!

---

### Post by geekdreams on 2005-08-17
*bump*

---

### Post by varunus on 2005-08-17
You can also just open a terminal, cd over to where the packages are, and type "sudo dpkg -i *.deb"

You may have to fix dependencies though...it will complain about some packages you don't have, go fetch those, burn to CD, and then install those in the same way.

---

### Post by geekdreams on 2005-08-18
dpkg appears to be really cranky about installing things in order, and for some reason apt-get still doesn't see the packages even when I copy them to the hard disk. :(

---

### Post by varunus on 2005-08-23
apt can't just see packages; it needs a repository, I think.

dpkg should work, just keep hammering at "sudo dpkg -i *" until all of the packages install.  Some may not install initially, but their dependencies will get installed eventually and it should work.

---

