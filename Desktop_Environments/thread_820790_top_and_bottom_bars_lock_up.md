---
title: "top and bottom bars lock up"
date: 2008-06-06
forum: Desktop Environments
---

### Post by billflanery on 2008-06-06
My top and bottom bars lock up after a while.  I can still use programs that are running and I can <alt><tab> to switch between them.  The only fix has been to reboot.

The bars appear to not refresh properly, because the now-running-programs tabs on the bottom bar will stay there for a while, then they get progressively more garbled, until they're just gray.  Similarly, the clock usually stays visible, but stops changing.

A couple icons on the top bar keep working (volume, Wired Network Connection, and Tracker (search tool). But everything else is frozen.

The problem started after a hard lockup of Feisty and a power-cycle restart.  I've since upgraded to Gutsy and now Hardy, but the problem is exactly the same.

Does anyone know what might be causing this?
What is the name of the program that controls the top and bottom bars?
Is there a log file that might give me some insight?

Thanks!

---

### Post by Mr_bleu on 2008-06-07
I thought this was a kde4 bug.  I had this issue last night after coming home from work.  I had left my laptop running all night/day.  I uninstalled kde4 and no problems since.  I am running kde 3.5.  I like that desktop.

---

### Post by tcommbee on 2008-06-07
Check the contents of the hidden file .xsession-errors in your home directory for errors relating to gnome-panel
Did you already try re-installing gnome-panel and gnome-panel-data?

---

### Post by billflanery on 2008-06-09
Thanks for the suggestion.  
It looks like Firefox may be the culprit.  I'm gonna reboot and try changing version (I'm at 5 Beta right now).


Here is what gets written to the .xsession-errors file when the toolbar crashes:

(firefox:6693): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6693): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6693): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6693): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6693): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6693): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6693): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6693): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Here's the entire file:

/etc/gdm/Xsession: Beginning session setup...
/etc/profile: 28: Optics/OmniDriverSPAM/OOI_HOME:/opt/Ocean: not found
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
SESSION_MANAGER=local/billflanery-dell9400laptop:/tmp/.ICE-unix/6274
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
Shutdown failed or nothing to shut down.
xrdb:  "*Label.background" on line 220 overrides entry on line 150
xrdb:  "*Text.background" on line 226 overrides entry on line 191
xrdb:  "*Label.foreground" on line 232 overrides entry on line 151
xrdb:  "*Text.foreground" on line 238 overrides entry on line 192
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: Failed to read saved session file /home/billflanery/.metacity/sessions/default0.ms: Failed to open file '/home/billflanery/.metacity/sessions/default0.ms': No such file or directory
11
ERROR: trackerd already running on your session dbus - exiting...
Initializing nautilus-share extension
seahorse nautilus module initialized
evolution-alarm-notify-Message: Setting timeout for 46451 1213070400 1213023949
evolution-alarm-notify-Message:  Tue Jun 10 00:00:00 2008

evolution-alarm-notify-Message:  Mon Jun  9 11:05:49 2008


** (nautilus:6394): WARNING **: Unable to add monitor: Not supported
  PID TTY          TIME CMD
 6372 ?        00:00:00 pulseaudio
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
Initializing nautilus-share extension

** (nautilus:6980): WARNING **: Unable to add monitor: Operation not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSNautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

---

