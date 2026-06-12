---
title: "Beryl crashed, can't startup again"
date: 2007-01-01
forum: Desktop Environments
---

### Post by Skyler0 on 2007-01-01
Okay, so I was fooling around with some of the settings in beryl, and the cube and what not, and then everything froze. I waited a bit to see if it would come back, or if I could do anything, but I couldn't. I tried Ctrl+Alt+Backspace, and that worked.

I went to re-login and what not, but got an error about gnome-session: 4747: GTK-Warning, cannot open display. It went back to the login screen, but then the screen had a dark blue screenish, and then alternated to the same blue but with horizontal black lines in it.

I restarted the computer with the button, and got the same error going into xgl, so I booted into gnome, and tried defaulting all the settings for beryl, but that didn't work.

So I'm not really sure what to do, and I help is very appreciated.

Also, here's the .xsesstion-errors log file, which may be of some help.

> /etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "sky"
/etc/gdm/Xsession: Beginning session setup...
/etc/profile: 20: [[: not found
SESSION_MANAGER=local/sky-ubuntu:/tmp/.ICE-unix/4834
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
** Message: error parsing desktop file for /apps/kiba/launchers/Do: /home/sky/.kiba-dock/Downloaded is not a .desktop file

evolution-alarm-notify-Message: Setting timeout for 60855 1167696000 1167635145
evolution-alarm-notify-Message:  Mon Jan  1 19:00:00 2007

evolution-alarm-notify-Message:  Mon Jan  1 02:05:45 2007

Unable to open desktop file file:///home/sky/Desktop/curly-00716e071d.desktop for panel launcher: No such file or directory

(gaim:4934): Pango-CRITICAL **: pango_font_description_set_absolute_size: assertion `size >= 0' failed
Traceback (most recent call last):
  File "/usr/share/apport/apport-gtk", line 165, in on_button_reportbug_clicked
    self.w('progressbar_information_collection').pulse()
AttributeError: 'NoneType' object has no attribute 'pulse'
checking for valid crashreport now
bad args to metacity-dialog
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1400069 (Buddy List)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

(gaim:5183): Pango-CRITICAL **: pango_font_description_set_absolute_size: assertion `size >= 0' failed
bad args to metacity-dialog
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1400069 (Buddy List)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.


---

