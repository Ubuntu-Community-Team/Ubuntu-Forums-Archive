---
title: "gnome screensaver failed to unlock"
date: 2007-06-07
forum: Desktop Environments
---

### Post by wiflye81 on 2007-06-07
Hi,

I have a strange bug with gnome-screensaver on feisty, I can't unlock screensaver, I may have installed an application which can cause the problem (but I haven't nothing so exotic and dangerous) because on a fresh installation, it works perfectly

Here is the log:

[gs_grab_move_keyboard] gs-grab-x11.c:326 (09:51:07):    Window 1600020 is already grabbed, skipping
[gs_grab_move_mouse] gs-grab-x11.c:266 (09:51:07):       Window 1600020 is already grabbed, skipping
[manager_maybe_start_job_for_window] gs-manager.c:198 (09:51:07):        Starting job for window
[gs_job_start] gs-job.c:431 (09:51:07):  starting job
[gs_job_start] gs-job.c:446 (09:51:07):  No command set for job.
[gs_window_xevent] gs-window-x11.c:669 (09:51:07):       not raising our windows
[unfade_idle] gs-manager.c:1150 (09:51:07):      resetting fade
[gs_fade_reset] gs-fade.c:634 (09:51:07):        Resetting fade
[find_window_at_pointer] gs-manager.c:1099 (09:51:12):   Requesting unlock for screen 0
[gs_window_request_unlock] gs-window-x11.c:1507 (09:51:12):      Requesting unlock
[window_dialog_up_cb] gs-manager.c:1008 (09:51:12):      Handling dialog up
[xorg_lock_smasher_set_active] gs-grab-x11.c:126 (09:51:12):     Disabling the x.org grab smasher
[xorg_lock_smasher_set_active] gs-grab-x11.c:146 (09:51:12):     XF86MiscSetGrabKeysState(off) returned MiscExtGrabStateAlready

[gs_grab_move_keyboard] gs-grab-x11.c:326 (09:51:12):    Window 1600020 is already grabbed, skipping
[gs_grab_move_mouse] gs-grab-x11.c:266 (09:51:12):       Window 1600020 is already grabbed, skipping
[gs_grab_release_mouse] gs-grab-x11.c:239 (09:51:12):    Ungrabbing pointer
[window_dialog_up_cb] gs-manager.c:1031 (09:51:12):      Suspending jobs
[gs_job_suspend] gs-job.c:508 (09:51:12):        suspending job
[popup_dialog_idle] gs-window-x11.c:1463 (09:51:12):     Popping up dialog
[gs_window_clear] gs-window-x11.c:274 (09:51:12):        Clearing window
[clear_all_children] gs-window-x11.c:249 (09:51:12):     Clearing all child windows
[get_env_vars] gs-window-x11.c:859 (09:51:12):   adding environment: PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/lib/gnome-screensaver/gnome-screensaver:/usr/lib/xscreensaver:/usr/lib/xscreensaver
[get_env_vars] gs-window-x11.c:859 (09:51:12):   adding environment: SESSION_MANAGER=local/lancelot-desktop:/tmp/.ICE-unix/5546
[get_env_vars] gs-window-x11.c:859 (09:51:12):   adding environment: XAUTHORITY=/home/gwenole/.Xauthority
[get_env_vars] gs-window-x11.c:859 (09:51:12):   adding environment: LANG=fr_FR.UTF-8
[get_env_vars] gs-window-x11.c:859 (09:51:12):   adding environment: LOGNAME=gwenole
[get_env_vars] gs-window-x11.c:859 (09:51:12):   adding environment: DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-Q3xPIxTdJi,guid=eac418bce46d2e664ac457004667a7b8
[error_watch] gs-window-x11.c:886 (09:51:13):    command error output: [gs_debug_init] gs-debug.c:106 (09:51:13):        Debugging enabled

[gs_manager_request_unlock] gs-manager.c:1552 (09:51:13):        Request unlock but dialog is already up
[error_watch] gs-window-x11.c:886 (09:51:13):    command error output: [auth_message_handler] gnome-screensaver-dialog.c:216 (09:51:13):         Got message style 1: 'Password: '

[gs_window_raise] gs-window-x11.c:598 (09:51:13):        Raising screensaver window
[gs_window_xevent] gs-window-x11.c:669 (09:51:13):       not raising our windows
[gs_window_xevent] gs-window-x11.c:669 (09:51:13):       not raising our windows
[gs_window_raise] gs-window-x11.c:598 (09:51:13):        Raising screensaver window
[lock_command_watch] gs-window-x11.c:1367 (09:51:13):    command output: WINDOW ID=75497475

[error_watch] gs-window-x11.c:886 (09:51:13):    command error output: [gs_lock_plug_enable_prompt] gs-lock-plug.c:839 (09:51:13):       Setting prompt to: Mot de passeÂ :

[gs_window_xevent] gs-window-x11.c:650 (09:51:13):       not raising our windows
[gs_window_raise] gs-window-x11.c:598 (09:51:13):        Raising screensaver window
[gs_window_xevent] gs-window-x11.c:650 (09:51:13):       not raising our windows
[gs_window_xevent] gs-window-x11.c:650 (09:51:13):       not raising our windows
[error_watch] gs-window-x11.c:886 (09:51:15):    command error output: [request_response] gnome-screensaver-dialog.c:144 (09:51:15):     got response: -2

[error_watch] gs-window-x11.c:886 (09:51:17):    command error output: [do_auth_check] gnome-screensaver-dialog.c:290 (09:51:17):        Verify user returned: FALSE

[lock_command_watch] gs-window-x11.c:1367 (09:51:17):    command output: NOTICE=AUTH FAILED

[error_watch] gs-window-x11.c:886 (09:51:17):    command error output: [do_auth_check] gnome-screensaver-dialog.c:293 (09:51:17):        Verify user returned error: L'authentification a Ã©chouÃ©.

[gs_window_raise] gs-window-x11.c:598 (09:51:17):        Raising screensaver window
[error_watch] gs-window-x11.c:886 (09:51:17):    command error output: [auth_message_handler] gnome-screensaver-dialog.c:216 (09:51:17):         Got message style 1: 'Password: '

[error_watch] gs-window-x11.c:886 (09:51:17):    command error output: [gs_lock_plug_enable_prompt] gs-lock-plug.c:839 (09:51:17):       Setting prompt to: Mot de passeÂ :

[gs_window_raise] gs-window-x11.c:598 (09:51:17):        Raising screensaver window
[gs_window_raise] gs-window-x11.c:598 (09:51:17):        Raising screensaver window
[gs_window_raise] gs-window-x11.c:598 (09:51:17):        Raising screensaver window
[gs_window_raise] gs-window-x11.c:598 (09:51:17):        Raising screensaver window
[gs_window_raise] gs-window-x11.c:598 (09:51:17):        Raising screensaver window
[gs_window_raise] gs-window-x11.c:598 (09:51:17):        Raising screensaver window
[gs_window_raise] gs-window-x11.c:598 (09:51:17):        Raising screensaver window
[gs_window_raise] gs-window-x11.c:598 (09:51:17):        Raising screensaver window

Hope it helps, I don't want to format this installation to find the culprit :(

---

### Post by jhallward on 2008-01-18
I'm having the exact same issue, but a reinstall is not an option.  Has anyone figured this out yet?

---

