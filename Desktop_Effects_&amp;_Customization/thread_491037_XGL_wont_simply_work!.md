---
title: "XGL wont simply work!"
date: 2007-07-03
forum: Desktop Effects &amp; Customization
---

### Post by SessionX on 2007-07-03
Alright, I'm on Gutsy (Ubuntu 7.10), and want CF and such, so I went on getting up a XGL session. I followed this guide: [Linky]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29") 

It's for Feisty, but I thought that didn't matter, and I droped the Beryl part, of course.

So when everything is set, looks like it did on Feisty (were it worked) I get an "Your session last less than 10 seconds" error. 

Here's my .xsession-errors file:

> 
(process:21955): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:21959): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "kasper"
/etc/gdm/Xsession: Beginning session setup...
/etc/X11/Xsession.d/40guidance-displayconfig_restore: 11: /usr/bin/displayconfig-restore: not found

***MEMORY-WARNING***: x-session-manager[21952]: GSlice: g_thread_init() must be called before all other GLib functions; memory corruption due to late invocation of g_thread_init() has been detected; this program is likely to crash, leak or unexpectedly abort soon...
SESSION_MANAGER=local/GutsyGibbon:/tmp/.ICE-unix/21952

** (process:21993): WARNING **: couldn't connect to dbus session bus: Failed to execute dbus-launch to autolaunch D-Bus session

***MEMORY-WARNING***: metacity[22013]: GSlice: g_thread_init() must be called before all other GLib functions; memory corruption due to late invocation of g_thread_init() has been detected; this program is likely to crash, leak or unexpectedly abort soon...
Window manager warning: Failed to read saved session file /home/kasper/.metacity/sessions/default0.ms: Failed to open file '/home/kasper/.metacity/sessions/default0.ms': No such file or directory
[: 99: ==: unexpected operator
Initializing gnome-mount extension
[: 99: ==: unexpected operator
** Message: Not starting remote desktop server
evolution-alarm-notify-Message: Setting timeout for 54052 1183507200 1183453148
evolution-alarm-notify-Message:  Wed Jul  4 02:00:00 2007

evolution-alarm-notify-Message:  Tue Jul  3 10:59:08 2007

Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

(gnome-panel:22086): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -3 and height 24

** (nm-applet:22085): WARNING **: <WARN>  nmi_save_network_info(): Error saving secret for wireless network 'Johns' in keyring: 1


***MEMORY-WARNING***: firefox-bin[22312]: GSlice: g_thread_init() must be called before all other GLib functions; memory corruption due to late invocation of g_thread_init() has been detected; this program is likely to crash, leak or unexpectedly abort soon...

***MEMORY-WARNING***: gnome-app-install[22520]: GSlice: g_thread_init() must be called before all other GLib functions; memory corruption due to late invocation of g_thread_init() has been detected; this program is likely to crash, leak or unexpectedly abort soon...

** (gnome-app-install:22520): WARNING **: return value of custom widget handler was not a GtkWidget
/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py:1154: GtkWarning: gtk_tree_model_sort_sort: assertion `tree_model_sort->default_sort_func != NULL' failed
  item.applications.set_default_sort_func(None)
/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py:1011: GtkWarning: gtk_tree_model_sort_sort: assertion `tree_model_sort->default_sort_func != NULL' failed
  model.set_default_sort_func(None)
Window manager warning: Window 0x280142c () sets an MWM hint indicating it isn't resizable, but sets min size 514 x 285 and max size 2147483647 x 2147483647; this doesn't make much sense.
Window manager warning: Window 0x280142c () sets an MWM hint indicating it isn't resizable, but sets min size 514 x 285 and max size 2147483647 x 2147483647; this doesn't make much sense.

***MEMORY-WARNING***: gksu[22537]: GSlice: g_thread_init() must be called before all other GLib functions; memory corruption due to late invocation of g_thread_init() has been detected; this program is likely to crash, leak or unexpectedly abort soon...
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

** (epiphany-browser:22704): WARNING **: No word lists can be found for the language "nb".

--- Hash table keys for warning below:
--> file:///home/kasper

(nautilus:23032): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time (keys above)

I think it's only the top part that has something, but.. 

Well, I hope for help.:D

---

