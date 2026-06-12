---
title: "Can't unlock screen"
date: 2009-01-05
forum: General Help
---

### Post by egates on 2009-01-05
Using ubuntu 8.10, fully up-to-date (just upgraded all the way from 7.04 to 8.10 over the weekend).

When using either gnome-screensaver (or xscreensaver), I am unable to unlock
my screen.  With gnome-screensaver the dialog box to unlock (or switch users, etc) appears, but when I enter my password I get a message saying
Incorrect Password.  As this affects more than one screen saver, I am suspecting a permissions error somewhere, but I don't have enough knowledge to know where or what the problem may be.  I am able to log into another session via switch user and kill the screensaver, thus getting my session back.

I ran gnome-screensaver --no-daemon --debug to try and figure out where the
problem may be.  Here is the relevent section of the output:

[gs_window_raise] gs-window-x11.c:728 (20:45:26):        Raising screensaver window
[gs_window_xevent] gs-window-x11.c:799 (20:45:26):       not raising our windows
[error_watch] gs-window-x11.c:959 (20:45:29):    command error output: [request_response] gnome-screensaver-dialog.c:149 (20:45:29):     got response: -2

[error_watch] gs-window-x11.c:959 (20:45:31):    command error output: [do_auth_check] gnome-screensaver-dialog.c:295 (20:45:31):        Verify user returned: FALSE

[error_watch] gs-window-x11.c:959 (20:45:31):    command error output: [do_auth_check] gnome-screensaver-dialog.c:298 (20:45:31):        Verify user returned error: Incorrect password.

[lock_command_watch] gs-window-x11.c:1431 (20:45:31):    command output: NOTICE=AUTH FAILED

[gs_window_move_resize_window] gs-window-x11.c:455 (20:45:31):   Move and/or resize window on monitor 0: x=1600 y=0 w=1600 h=1200
[error_watch] gs-window-x11.c:959 (20:45:31):    command error output: [auth_check_idle] gnome-screensaver-dialog.c:342 (20:45:31):      Authentication failed, retrying (2)



I found this output not very helpful, though maybe someone familiar with gnome-screensaver's code will be able to narrow down what the problem is.  Since this is an office machine, it is important to be able to lock the session (and recover) easily.

---

