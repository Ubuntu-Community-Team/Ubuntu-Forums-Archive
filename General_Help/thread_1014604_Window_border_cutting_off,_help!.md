---
title: "Window border cutting off, help!"
date: 2008-12-18
forum: General Help
---

### Post by Rylin on 2008-12-18
Whenever I open up any program or application window, it opens up the window at the top left of the desktop and it cuts off the window border. The only way to move the window is to right click the app window in the gnome panel tray and move it.

Any ideas on how to fix this? :confused:

---

### Post by pietjanjaap on 2008-12-18
Advanced desktop effects settings window decoration, another guy switch this off and then onn and then it works(with every reboot).

I think it has something to do compiz, that is not configured good, so you need to install/configure your videocard drivers.

You could also disable compiz, to see if it works.

Monday, April 14, 2008
Stop Compiz-Fusion From Loading Automatically

This guide will show you how to stop Compiz-Fusion from loading automatically on startup in Hardy Heron and how to setup a shortcut for launching Compiz when you want.

Step 1: Run gconf-edit
Start Run Application by pressing Alt+F2

Screenshot-Run Application

Enter gconf-editor into the box, hit enter


Step 2: Set Metacity as your default start up window manager
Once in gconf-editor navigate to desktop>gnome>applications>window_manager

Screenshot-Configuration Editor - window_manager

under current and default replace each instance of:
/usr/bin/compiz with /usr/bin/metacity
it should like this when you're done:

Screenshot-Configuration Editor - window_manager-1



Step 3: Create a shortcut for starting Compiz-Fusion
right click the Applications Places System Menu
select the Edit Menu option

Screenshot-Main Menu

pick a location for your shortcut and select New Item box

Screenshot-Launcher Properties
Type: Application
Name: Compiz
Command: compiz --replace
COmment compiz window manager

---

