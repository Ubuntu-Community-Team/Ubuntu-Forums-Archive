---
title: "gnome-screensaver on dual monitor with laptop monitor off"
date: 2010-02-09
forum: Desktop Environments
---

### Post by raghu1111 on 2010-02-09
gnome-screensaver set to slideshow. 5 min idle and monitor is set to go to stand by after 15min.

Hardware : Lenovo T400 on 'Advanced Mini Dock'. Dock is connection to a 1920x1200 LCD. Running with ATI binary modules for Radeon 3400.

When both laptop monitor and external monitor are on, screensaver runs well. Both monitors go to standby as expected.

But when laptop monitor set to "off" in Display options, screensaver does not work well. The external monitor does not go to standby. The slideshow sometimes starts, sometimes does not.

Using xset to put monitor to standby works fine.

thanks in advance.

---

### Post by raghu1111 on 2010-02-09
Just a clarification : screen goes blank, but monitor stays on.

---

### Post by raghu1111 on 2010-02-11
Log from 'gnome-screensaver --debug --no-daemon' is attached below.

settings : 
Screensaver : Blank Screen  
Regard idle after : 1 min 
Put display to sleep (in power management) : 5 min 

In another output from another computer, there seems to be some communication between gnome-power-manager. But there is none here.

```

[gs_debug_init] gs-debug.c:106 (20:14:43):       Debugging enabled
[main] gnome-screensaver.c:87 (20:14:43):        initializing gnome-screensaver 2.28.0
[init_session_id] gs-listener-dbus.c:1979 (20:14:43):    Got session-id: /org/freedesktop/ConsoleKit/Session2
[gs_fade_init] gs-fade.c:694 (20:14:43):         Fade type: 2
[set_status] gs-watcher-x11.c:345 (20:14:43):    GSWatcher: not active, ignoring status changes
[gs_watcher_set_active] gs-watcher-x11.c:275 (20:14:43):         turning watcher: ON
[listener_dbus_handle_system_message] gs-listener-dbus.c:1404 (20:14:43):        obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameAcquired destination=:1.105
[listener_service_deleted] gs-listener-dbus.c:1042 (20:14:43):   DBUS service deleted:
[listener_dbus_handle_system_message] gs-listener-dbus.c:1404 (20:14:43):        obj_path=(null) interface=(null) method=(null) destination=:1.105
[listener_dbus_handle_system_message] gs-listener-dbus.c:1404 (20:14:43):        obj_path=(null) interface=(null) method=(null) destination=:1.105
[listener_dbus_handle_system_message] gs-listener-dbus.c:1404 (20:14:43):        obj_path=(null) interface=(null) method=(null) destination=:1.105
[listener_dbus_handle_system_message] gs-listener-dbus.c:1404 (20:14:43):        obj_path=(null) interface=(null) method=(null) destination=:1.105
[on_bg_changed] gs-manager.c:953 (20:14:43):     background changed

[...]
[listener_service_deleted] gs-listener-dbus.c:1042 (20:18:01):   DBUS service deleted: :1.179
[listener_service_deleted] gs-listener-dbus.c:1042 (20:18:01):   DBUS service deleted: :1.180
[listener_service_deleted] gs-listener-dbus.c:1042 (20:18:01):   DBUS service deleted: :1.181
[listener_service_deleted] gs-listener-dbus.c:1042 (20:18:16):   DBUS service deleted:
[listener_service_deleted] gs-listener-dbus.c:1042 (20:18:16):   DBUS service deleted:
[listener_service_deleted] gs-listener-dbus.c:1042 (20:18:16):   DBUS service deleted: :1.182
[listener_service_deleted] gs-listener-dbus.c:1042 (20:18:16):   DBUS service deleted: :1.183
[watcher_idle_notice_cb] gs-monitor.c:125 (20:19:33):    Idle notice signal detected: 1
[gs_grab_grab_offscreen] gs-grab-x11.c:515 (20:19:33):   Grabbing an offscreen window
[gs_grab_get_keyboard] gs-grab-x11.c:171 (20:19:33):     Grabbing keyboard widget=2A00003
[gs_grab_get_mouse] gs-grab-x11.c:198 (20:19:33):        Grabbing mouse widget=2A00003
[gamma_info_init] gs-fade.c:345 (20:19:33):      Initialized gamma ramp fade
[_gs_watcher_set_session_idle_notice] gs-watcher-x11.c:202 (20:19:33):   Changing idle notice state: 1
[watcher_idle_cb] gs-monitor.c:95 (20:19:43):    Idle signal detected: 1
[gs_listener_set_session_idle] gs-listener-dbus.c:441 (20:19:43):        Setting session idle: 1
[listener_check_activation] gs-listener-dbus.c:310 (20:19:43):   Checking for activation
[listener_check_activation] gs-listener-dbus.c:325 (20:19:43):   Trying to activate
[gs_grab_grab_root] gs-grab-x11.c:496 (20:19:43):        Grabbing the root window
[gs_grab_get_keyboard] gs-grab-x11.c:171 (20:19:43):     Grabbing keyboard widget=AF
[gs_grab_get_mouse] gs-grab-x11.c:198 (20:19:43):        Grabbing mouse widget=AF
[gs_manager_create_windows_for_screen] gs-manager.c:1598 (20:19:43):     Creating 1 windows for screen 0
[gs_manager_create_window_for_monitor] gs-manager.c:1443 (20:19:43):     Creating window for monitor 0 [0,0] (1920x1200)
[gs_manager_activate] gs-manager.c:1707 (20:19:43):      fading out
[fade_done_cb] gs-manager.c:1668 (20:19:43):     fade completed, showing windows
[update_geometry] gs-window-x11.c:424 (20:19:43):        got geometry for monitor 0: x=0 y=0 w=1920 h=1200
[update_geometry] gs-window-x11.c:437 (20:19:43):        using geometry for monitor 0: x=0 y=0 w=1920 h=1200
[get_best_visual_for_screen] gs-window-x11.c:616 (20:19:43):     Found best GL visual for screen 0: 0x27
[gs_window_move_resize_window] gs-window-x11.c:470 (20:19:43):   Move and/or resize window on monitor 0: x=0 y=0 w=1920 h=1200
[window_map_cb] gs-manager.c:1259 (20:19:43):    Handling window map event
[clear_widget] gs-window-x11.c:344 (20:19:43):   Clearing widget
[widget_clear_all_children] gs-window-x11.c:256 (20:19:43):      Clearing all child windows
[clear_widget] gs-window-x11.c:344 (20:19:43):   Clearing widget
[widget_clear_all_children] gs-window-x11.c:256 (20:19:43):      Clearing all child windows
[window_show_cb] gs-manager.c:1337 (20:19:43):   Handling window show
[apply_background_to_window] gs-manager.c:1286 (20:19:43):       Creating pixmap background w:1920 h:1200
[gs_job_set_command] gs-job.c:193 (20:19:43):    Setting command for job: 'NULL'
[gs_watcher_set_active] gs-watcher-x11.c:275 (20:19:43):         turning watcher: OFF
[gs_listener_send_signal_active_changed] gs-listener-dbus.c:220 (20:19:43):      Sending the ActiveChanged(TRUE) signal on the session bus
[_gs_watcher_set_session_idle] gs-watcher-x11.c:225 (20:19:43):  Changing idle state: 1
[gs_window_xevent] gs-window-x11.c:795 (20:19:43):       not raising our windows
[window_map_event_cb] gs-manager.c:1246 (20:19:43):      Handling window map_event event
[manager_maybe_grab_window] gs-manager.c:1200 (20:19:43):        Moving grab to 0x886d178
[xorg_lock_smasher_set_active] gs-grab-x11.c:124 (20:19:43):     No XFree86-Misc extension present
[gs_grab_move_keyboard] gs-grab-x11.c:336 (20:19:43):    Moving keyboard grab from AF to 2A00060
[gs_grab_move_keyboard] gs-grab-x11.c:343 (20:19:43):    *** doing X server grab
[gs_grab_release_keyboard] gs-grab-x11.c:224 (20:19:43):         Ungrabbing keyboard
[gs_grab_get_keyboard] gs-grab-x11.c:171 (20:19:43):     Grabbing keyboard widget=2A00060
[gs_grab_move_keyboard] gs-grab-x11.c:365 (20:19:43):    *** releasing X server grab
[gs_grab_move_mouse] gs-grab-x11.c:281 (20:19:43):       Moving pointer grab from AF to 2A00060
[gs_grab_move_mouse] gs-grab-x11.c:288 (20:19:43):       *** doing X server grab
[gs_grab_release_mouse] gs-grab-x11.c:242 (20:19:43):    Ungrabbing pointer
[gs_grab_get_mouse] gs-grab-x11.c:198 (20:19:43):        Grabbing mouse widget=2A00060
[gs_grab_move_mouse] gs-grab-x11.c:311 (20:19:43):       *** releasing X server grab
[manager_maybe_start_job_for_window] gs-manager.c:215 (20:19:43):        Starting job for window
[gs_job_start] gs-job.c:435 (20:19:43):  starting job
[gs_job_start] gs-job.c:450 (20:19:43):  No command set for job.
[gs_window_xevent] gs-window-x11.c:795 (20:19:43):       not raising our windows
[window_map_event_cb] gs-manager.c:1246 (20:19:43):      Handling window map_event event
[manager_maybe_grab_window] gs-manager.c:1200 (20:19:43):        Moving grab to 0x886d178
[xorg_lock_smasher_set_active] gs-grab-x11.c:124 (20:19:43):     No XFree86-Misc extension present
[gs_grab_move_keyboard] gs-grab-x11.c:329 (20:19:43):    Window 2A00060 is already grabbed, skipping
[gs_grab_move_mouse] gs-grab-x11.c:269 (20:19:43):       Window 2A00060 is already grabbed, skipping
[manager_maybe_start_job_for_window] gs-manager.c:215 (20:19:43):        Starting job for window
[gs_job_start] gs-job.c:435 (20:19:43):  starting job
[gs_job_start] gs-job.c:450 (20:19:43):  No command set for job.
[gs_window_xevent] gs-window-x11.c:795 (20:19:43):       not raising our windows
[update_geometry] gs-window-x11.c:424 (20:19:43):        got geometry for monitor 0: x=0 y=0 w=1920 h=1200
[update_geometry] gs-window-x11.c:437 (20:19:43):        using geometry for monitor 0: x=0 y=0 w=1920 h=1200
[gs_window_move_resize_window] gs-window-x11.c:470 (20:19:43):   Move and/or resize window on monitor 0: x=0 y=0 w=1920 h=1200
[unfade_idle] gs-manager.c:1227 (20:19:44):      resetting fade
[gs_fade_reset] gs-fade.c:648 (20:19:44):        Resetting fade
[find_window_at_pointer] gs-manager.c:1176 (20:19:47):   Requesting unlock for screen 0
[gs_window_request_unlock] gs-window-x11.c:1626 (20:19:47):      Requesting unlock
[gs_fade_reset] gs-fade.c:648 (20:19:47):        Resetting fade
[gs_grab_release] gs-grab-x11.c:393 (20:19:47):  Releasing all grabs
[gs_grab_release_mouse] gs-grab-x11.c:242 (20:19:47):    Ungrabbing pointer
[gs_grab_release_keyboard] gs-grab-x11.c:224 (20:19:47):         Ungrabbing keyboard
[xorg_lock_smasher_set_active] gs-grab-x11.c:124 (20:19:47):     No XFree86-Misc extension present
[gs_job_stop] gs-job.c:483 (20:19:47):   stopping job
[gs_job_stop] gs-job.c:486 (20:19:47):   Could not stop job: pid not defined
[window_unmap_cb] gs-manager.c:1266 (20:19:47):  window unmapped!
[gs_window_dialog_finish] gs-window-x11.c:1374 (20:19:47):       Dialog finished
[keyboard_command_finish] gs-window-x11.c:1249 (20:19:47):       Keyboard finished
[gs_watcher_set_active] gs-watcher-x11.c:275 (20:19:47):         turning watcher: ON
[gs_listener_send_signal_active_changed] gs-listener-dbus.c:220 (20:19:47):      Sending the ActiveChanged(FALSE) signal on the session bus
[watcher_idle_notice_cb] gs-monitor.c:125 (20:21:14):    Idle notice signal detected: 1
[gs_grab_grab_offscreen] gs-grab-x11.c:515 (20:21:14):   Grabbing an offscreen window
[gs_grab_get_keyboard] gs-grab-x11.c:171 (20:21:14):     Grabbing keyboard widget=2A00003
[gs_grab_get_mouse] gs-grab-x11.c:198 (20:21:14):        Grabbing mouse widget=2A00003
[gamma_info_init] gs-fade.c:345 (20:21:14):      Initialized gamma ramp fade
[_gs_watcher_set_session_idle_notice] gs-watcher-x11.c:202 (20:21:14):   Changing idle notice state: 1
[watcher_idle_cb] gs-monitor.c:95 (20:21:24):    Idle signal detected: 1
[gs_listener_set_session_idle] gs-listener-dbus.c:441 (20:21:24):        Setting session idle: 1
[listener_check_activation] gs-listener-dbus.c:310 (20:21:24):   Checking for activation
[listener_check_activation] gs-listener-dbus.c:325 (20:21:24):   Trying to activate
[gs_grab_grab_root] gs-grab-x11.c:496 (20:21:24):        Grabbing the root window
[gs_grab_get_keyboard] gs-grab-x11.c:171 (20:21:24):     Grabbing keyboard widget=AF
[gs_grab_get_mouse] gs-grab-x11.c:198 (20:21:24):        Grabbing mouse widget=AF
[gs_manager_create_windows_for_screen] gs-manager.c:1598 (20:21:24):     Creating 1 windows for screen 0
[gs_manager_create_window_for_monitor] gs-manager.c:1443 (20:21:24):     Creating window for monitor 0 [0,0] (1920x1200)
[gs_manager_activate] gs-manager.c:1707 (20:21:24):      fading out
[fade_done_cb] gs-manager.c:1668 (20:21:24):     fade completed, showing windows
[update_geometry] gs-window-x11.c:424 (20:21:24):        got geometry for monitor 0: x=0 y=0 w=1920 h=1200
[update_geometry] gs-window-x11.c:437 (20:21:24):        using geometry for monitor 0: x=0 y=0 w=1920 h=1200
[get_best_visual_for_screen] gs-window-x11.c:616 (20:21:24):     Found best GL visual for screen 0: 0x27
[gs_window_move_resize_window] gs-window-x11.c:470 (20:21:24):   Move and/or resize window on monitor 0: x=0 y=0 w=1920 h=1200
[window_map_cb] gs-manager.c:1259 (20:21:24):    Handling window map event
[clear_widget] gs-window-x11.c:344 (20:21:24):   Clearing widget
[widget_clear_all_children] gs-window-x11.c:256 (20:21:24):      Clearing all child windows
[clear_widget] gs-window-x11.c:344 (20:21:24):   Clearing widget
[widget_clear_all_children] gs-window-x11.c:256 (20:21:24):      Clearing all child windows
[window_show_cb] gs-manager.c:1337 (20:21:24):   Handling window show
[apply_background_to_window] gs-manager.c:1286 (20:21:24):       Creating pixmap background w:1920 h:1200
[gs_job_set_command] gs-job.c:193 (20:21:24):    Setting command for job: 'NULL'
[gs_watcher_set_active] gs-watcher-x11.c:275 (20:21:24):         turning watcher: OFF
[gs_listener_send_signal_active_changed] gs-listener-dbus.c:220 (20:21:24):      Sending the ActiveChanged(TRUE) signal on the session bus
[_gs_watcher_set_session_idle] gs-watcher-x11.c:225 (20:21:24):  Changing idle state: 1
[gs_window_xevent] gs-window-x11.c:795 (20:21:24):       not raising our windows
[window_map_event_cb] gs-manager.c:1246 (20:21:24):      Handling window map_event event
[manager_maybe_grab_window] gs-manager.c:1200 (20:21:24):        Moving grab to 0x886d2b8
[xorg_lock_smasher_set_active] gs-grab-x11.c:124 (20:21:24):     No XFree86-Misc extension present
[gs_grab_move_keyboard] gs-grab-x11.c:336 (20:21:24):    Moving keyboard grab from AF to 2A00098
[gs_grab_move_keyboard] gs-grab-x11.c:343 (20:21:24):    *** doing X server grab
[gs_grab_release_keyboard] gs-grab-x11.c:224 (20:21:24):         Ungrabbing keyboard
[gs_grab_get_keyboard] gs-grab-x11.c:171 (20:21:24):     Grabbing keyboard widget=2A00098
[gs_grab_move_keyboard] gs-grab-x11.c:365 (20:21:24):    *** releasing X server grab
[gs_grab_move_mouse] gs-grab-x11.c:281 (20:21:24):       Moving pointer grab from AF to 2A00098
[gs_grab_move_mouse] gs-grab-x11.c:288 (20:21:24):       *** doing X server grab
[gs_grab_release_mouse] gs-grab-x11.c:242 (20:21:24):    Ungrabbing pointer
[gs_grab_get_mouse] gs-grab-x11.c:198 (20:21:24):        Grabbing mouse widget=2A00098
[gs_grab_move_mouse] gs-grab-x11.c:311 (20:21:24):       *** releasing X server grab
[manager_maybe_start_job_for_window] gs-manager.c:215 (20:21:24):        Starting job for window
[gs_job_start] gs-job.c:435 (20:21:24):  starting job
[gs_job_start] gs-job.c:450 (20:21:24):  No command set for job.
[gs_window_xevent] gs-window-x11.c:795 (20:21:24):       not raising our windows
[window_map_event_cb] gs-manager.c:1246 (20:21:24):      Handling window map_event event
[manager_maybe_grab_window] gs-manager.c:1200 (20:21:24):        Moving grab to 0x886d2b8
[xorg_lock_smasher_set_active] gs-grab-x11.c:124 (20:21:24):     No XFree86-Misc extension present
[gs_grab_move_keyboard] gs-grab-x11.c:329 (20:21:24):    Window 2A00098 is already grabbed, skipping
[gs_grab_move_mouse] gs-grab-x11.c:269 (20:21:24):       Window 2A00098 is already grabbed, skipping
[manager_maybe_start_job_for_window] gs-manager.c:215 (20:21:24):        Starting job for window
[gs_job_start] gs-job.c:435 (20:21:24):  starting job
[gs_job_start] gs-job.c:450 (20:21:24):  No command set for job.
[gs_window_xevent] gs-window-x11.c:795 (20:21:24):       not raising our windows
[update_geometry] gs-window-x11.c:424 (20:21:24):        got geometry for monitor 0: x=0 y=0 w=1920 h=1200
[update_geometry] gs-window-x11.c:437 (20:21:24):        using geometry for monitor 0: x=0 y=0 w=1920 h=1200
[gs_window_move_resize_window] gs-window-x11.c:470 (20:21:24):   Move and/or resize window on monitor 0: x=0 y=0 w=1920 h=1200
[unfade_idle] gs-manager.c:1227 (20:21:25):      resetting fade
[gs_fade_reset] gs-fade.c:648 (20:21:25):        Resetting fade
[gs_manager_cycle] gs-manager.c:645 (20:31:24):  cycling jobs
[gs_job_stop] gs-job.c:483 (20:31:24):   stopping job
[gs_job_stop] gs-job.c:486 (20:31:24):   Could not stop job: pid not defined
[gs_job_set_command] gs-job.c:193 (20:31:24):    Setting command for job: 'NULL'
[manager_maybe_start_job_for_window] gs-manager.c:215 (20:31:24):        Starting job for window
[gs_job_start] gs-job.c:435 (20:31:24):  starting job
[gs_job_start] gs-job.c:450 (20:31:24):  No command set for job.
[find_window_at_pointer] gs-manager.c:1176 (20:32:29):   Requesting unlock for screen 0
[gs_window_request_unlock] gs-window-x11.c:1626 (20:32:29):      Requesting unlock
[gs_fade_reset] gs-fade.c:648 (20:32:29):        Resetting fade
[gs_grab_release] gs-grab-x11.c:393 (20:32:29):  Releasing all grabs
[gs_grab_release_mouse] gs-grab-x11.c:242 (20:32:29):    Ungrabbing pointer
[gs_grab_release_keyboard] gs-grab-x11.c:224 (20:32:29):         Ungrabbing keyboard
[xorg_lock_smasher_set_active] gs-grab-x11.c:124 (20:32:29):     No XFree86-Misc extension present
[gs_job_stop] gs-job.c:483 (20:32:29):   stopping job
[gs_job_stop] gs-job.c:486 (20:32:29):   Could not stop job: pid not defined
[window_unmap_cb] gs-manager.c:1266 (20:32:29):  window unmapped!
[gs_window_dialog_finish] gs-window-x11.c:1374 (20:32:29):       Dialog finished
[keyboard_command_finish] gs-window-x11.c:1249 (20:32:29):       Keyboard finished
[gs_watcher_set_active] gs-watcher-x11.c:275 (20:32:29):         turning watcher: ON
[gs_listener_send_signal_active_changed] gs-listener-dbus.c:220 (20:32:29):      Sending the ActiveChanged(FALSE) signal on the session bus

```

---

### Post by Stan-O on 2010-02-17
Hi, I have samsung laptop and I have noticed the same behavior described here. If I switch from internal display to external one and then close the lid of the laptop then screensaver only shows blank screen instead of selected theme. If I open the lid while screensaver is still on then the selected screensaver theme is activated and stays on after I close the lid. If I stop the screensaver by moving mouse and let it start again while lid is closed only blank screen is activated. Also Gnome-Power-manager doesn't switch off external display after the idle time set in the parameters, the external display stays always on if I close the lid of the laptop or switch off internal display. There must be some logic in gnome-screensaver and gnome-power-manager that looks if laptop internal screen is off or if the lid is closed and then it does not activate screensaver or DPMS features because they are not needed. Problem is that if one uses external display with internal laptop display swithced off or lid closed screensaver should be activated and DPMS should still work for external display. I think gnome-screenasver and gnome-power-manager code should be changed to become aware of the display that is being used and if the external display is used they should ignore on/off status of internal display or lid position.

---

### Post by raghu1111 on 2010-02-23
gnome-power-manager and gnome-screensaver seem to be very confused by the closed lid. Looks like gnome-power-manager does not function once the lid is closed. gnome-screensaver at least starts the screensaver on the external monitor most of the time. I implemented a poor-mans version of screensaver management. I am running the following script every minute in crontab. manual-screensaver.sh :

```

#!/bin/bash

# this is a workaround for screensaver problems with external monotor 
# on lenovo. gnome-screensaver and gnome-power-manager seem to get 
# confused since the laptop screen is disabled and the lid is closed.

export DISPLAY=:0.0
SCREENSAVER=300000 #milliseconds
DISPLAYSTANDBY=600000

SS_STATE=`gnome-screensaver-command -q`

ss_is() {
    [[ "${SS_STATE}" =~ "The screensaver is $1" ]]
}

ss_is 'being inhibited' && exit

IDLE=`xprintidle` # in milliseconds

[ $IDLE -lt $SCREENSAVER ] && exit

if [ $IDLE -lt $DISPLAYSTANDBY ] ; then
   ss_is active || gnome-screensaver-command -a
elif ss_is active ; then
   gnome-screensaver-command -d
   xset dpms force standby
fi


```

In the screensaver configuration set the screensaver to start slightly later.

---

