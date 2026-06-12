---
title: "Tint2 wm_menu Not Working"
date: 2011-07-27
forum: Desktop Environments
---

### Post by mooreted on 2011-07-27
Currently running Ubuntu 10.04 with OpenBox and Tint2 from the repos.

I use the same setup on 3 computers; one with Ubuntu 11.04, one with 10.04 and one with Debian 6. The Tint2 wm_menu setting works on all but the 10.04 system. 

Do I need to go compile Tint2 from source or is there a way to get "wm_menu = 1" to work?

Here's my tint2rc:


#---------------------------------------------
# TINT2 CONFIG FILE
#---------------------------------------------

#---------------------------------------------
# BACKGROUND AND BORDER
#---------------------------------------------
rounded = 7
border_width = 2
background_color = #000000 60
border_color = #ffffff 18

rounded = 5
border_width = 0
background_color = #ffffff 40
border_color = #ffffff 50

rounded = 5
border_width = 0
background_color = #ffffff 18
border_color = #ffffff 70

#---------------------------------------------
# PANEL
#---------------------------------------------
panel_monitor = all
panel_position = bottom center
panel_size = 94% 30
panel_margin = 0 0
panel_padding = 7 0
font_shadow = 0
panel_background_id = 1
wm_menu = 1

#---------------------------------------------
# TASKBAR
#---------------------------------------------
#taskbar_mode = multi_desktop
taskbar_mode = single_desktop
taskbar_padding = 2 3 2
taskbar_background_id = 0

#---------------------------------------------
# TASKS
#---------------------------------------------
task_icon = 1
task_text = 1
task_width = 140
task_centered = 1
task_padding = 6 3
task_font = sans 7
task_font_color = #ffffff 70
task_active_font_color = #ffffff 85
task_background_id = 3
task_active_background_id = 2

#---------------------------------------------
# SYSTRAYBAR
#---------------------------------------------
systray_padding = 0 4 5
systray_background_id = 0

#---------------------------------------------
# CLOCK
#---------------------------------------------
time1_format = %r
time1_font = sans 8
time2_format = %A %d %B
time2_font = sans 6
clock_font_color = #ffffff 76
clock_padding = 1 0
clock_background_id = 0
#clock_lclick_command = xclock
clock_rclick_command = orage

#---------------------------------------------
# BATTERY
#---------------------------------------------
battery = 0
battery_low_status = 10
battery_low_cmd = notify-send "battery low"
bat1_font = sans 8
bat2_font = sans 6
battery_font_color = #ffffff 76
battery_padding = 1 0
battery_background_id = 0


#---------------------------------------------
# MOUSE ACTION ON TASK
#---------------------------------------------
mouse_middle = none
mouse_right = close
mouse_scroll_up = toggle
mouse_scroll_down = iconify

---

### Post by mooreted on 2011-07-28
Well, no one here seems to know either. It is kind of weird.

Guess I will get the latest Tint2 and compile it and see if that helps.

---

