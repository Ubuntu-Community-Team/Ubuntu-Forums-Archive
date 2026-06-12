---
title: "No systray in tint2"
date: 2009-11-01
forum: Desktop Environments
---

### Post by VCoolio on 2009-11-01
I'm probably overlooking something really stupid, but I've configured ( /tried to configure/) tint2 panel to show a systray but it doesn't, without error output. I've compiled it from svn (version 247) in Karmic, using openbox. It worked in Jaunty, so I'm really puzzled. My config:

```
#---------------------------------------------
# TINT2 CONFIG FILE
#---------------------------------------------
# For more information about tint2, see:
# http://code.google.com/p/tint2/wiki/Welcome
#
# For more config file examples, see:
# http://crunchbanglinux.org/forums/topic/3232/my-tint2-config/
#---------------------------------------------
# BACKGROUND AND BORDER
#---------------------------------------------
rounded = 5
border_width = 1
background_color = #000000 50
border_color = #FFFFFF 40

rounded = 3
border_width = 0
background_color = #ffffff 40
border_color = #ffffff 30

rounded = 3
border_width = 1
background_color = #ffffff 0
border_color = #ffffff 0

rounded = 0
border_width = 0
background_color = #000000 50
border_color = #ffffff 0

#---------------------------------------------
# PANEL
#---------------------------------------------
panel_monitor = all
panel_position = bottom right
panel_size = 0 34 	#width (0 = 100%) hight
panel_margin = 0 0
panel_padding = 3 3
font_shadow = 0
panel_background_id = 0
wm_menu = 1
#---------------------------------------------
# TASKBAR
#---------------------------------------------
taskbar_mode = multi_desktop
taskbar_padding = 2 2 2
taskbar_background_id = 1

#---------------------------------------------
# TASKS
#---------------------------------------------
task_icon = 1
task_text = 1
task_width = 150
task_centered = 0
task_padding = 2 2 2
task_font = sans 8
task_font_color = #ffffff 70
task_active_font_color = #ffffff 100
task_background_id = 3
task_active_background_id = 2

#---------------------------------------------
# SYSTRAYBAR
#---------------------------------------------
systray_padding = 4 2 3
systray_background_id = 3

#---------------------------------------------
# CLOCK
#---------------------------------------------
time1_format = %d/%m @ %H:%M 
time1_font = sans 8
time2_format = 
time2_font = sans 7
clock_font_color = #ffffff 100
clock_padding = 4 4 4
clock_background_id = 1

#---------------------------------------------
# BATTERY
#---------------------------------------------
#battery = 0
#battery_low_status = 7
#battery_low_cmd = notify-send "battery low"
#bat1_font = sans 8
#bat2_font = sans 6
#battery_font_color = #ffffff 76
#battery_padding = 1 0
#battery_background_id = 2


#---------------------------------------------
# MOUSE ACTION ON TASK
#---------------------------------------------
mouse_middle = close
mouse_right = none
mouse_scroll_up = toggle
mouse_scroll_down = iconify

```

---

### Post by thil77 on 2009-11-03
add to your config file
> 
systray = 1


of course svn is in developpement :)

---

