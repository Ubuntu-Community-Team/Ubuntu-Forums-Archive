---
title: "No Menubar"
date: 2007-12-21
forum: Desktop Effects &amp; Customization
---

### Post by vandenhout on 2007-12-21
Im new to ubuntu and none of the windows i open have a menubar.
could someone please help me get a menubar?

---

### Post by tgilber1 on 2007-12-21
Are you missing the titlebar on all your applications?  In any event, try opening linux terminal

#Applications#Assessories#Terminal

Type "metacity &"

If you get a no command not found error, then metacity is not installed skip down to the installation instructions below.  If metacity command executes, then does the metacity command fix the problem?  If so, follow the instructions below to make sure that metacity is the current and default window manager.

make sure that metacity is installed and it is your current and default window manager

dpkg -l metacity

if not installed, type "sudo apt-get install metacity"

Next, change the default and current window manager by using gconftool-2

gconftool-2 --set --type string /desktop/gnome/applications/window_manager/current metacity

gconftool-2 --set --type string /desktop/gnome/applications/window_manager/default metacity

You can verify that the settings took by the following command:

gconftool-2 --get /desktop/gnome/applications/window_manager/default
gconftool-2 --get /desktop/gnome/applications/window_manager/current

Finally, log out system and log back in; window manager should now be metacity.

---

