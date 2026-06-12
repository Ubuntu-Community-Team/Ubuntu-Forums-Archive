---
title: "Openbox, funky tint2 behavior; little help troubleshooting, plz"
date: 2010-01-01
forum: Desktop Environments
---

### Post by mailman1175 on 2010-01-01
Openbox in Karmic, with tint2.

I've got tint2 attached to the system tray, at the bottom of the screen, and it's set to autohide. It's supposed to be transparent. When I mouse over the tray, though, it has an artifact from the TOP of the screen/wallpaper embedded in it. [screenshot below]

Here's my tint2rc:

```
#---------------------------------------------
# TINT2 CONFIG FILE
#---------------------------------------------

#---------------------------------------------
# BACKGROUND AND BORDER
#---------------------------------------------
rounded = 7
border_width = 0
background_color = #000000 0
border_color = #ffffff 18

rounded = 5
border_width = 1
background_color = #ffffff 40
border_color = #ffffff 50

rounded = 5
border_width = 1
background_color = #ffffff 18
border_color = #ffffff 70

#---------------------------------------------
# PANEL
#---------------------------------------------
panel_monitor = all
panel_position = bottom center
panel_size = 95% 26
panel_margin = 0 0
panel_padding = 7 0
font_shadow = 0
panel_background_id = 0
wm_menu = 0
panel_dock = 1

#---------------------------------------------
# TASKBAR
#---------------------------------------------
#taskbar_mode = multi_desktop
taskbar_mode = single_desktop
taskbar_padding = 2 3 2
taskbar_background_id = 0
taskbar_active_background_id = 0

#---------------------------------------------
# TASKS
#---------------------------------------------
task_icon = 1
task_text = 0
# task_maximum_size = 140 35
task_width = 40
task_centered = 1
task_padding = 2 2
task_font = sans 7
task_font_color = #ffffff 70
task_active_font_color = #ffffff 85
task_background_id = 3
task_active_background_id = 2

#---------------------------------------------
# SYSTRAYBAR
#---------------------------------------------
systray = 1
systray_padding = 4 2 3
systray_background_id = 0
systray_sort = left2right

#---------------------------------------------
# CLOCK
#---------------------------------------------
time1_format = %r
time1_font = sans 7
time2_format = %A %D
time2_font = sans 6
clock_font_color = #ffffff 76
clock_padding = 1 0
clock_background_id = 0
clock_lclick_command = xclock
clock_rclick_command = orage
#clock_tooltip = %A %d %B

#---------------------------------------------
# BATTERY
#---------------------------------------------
battery = 0
battery_low_status = 20
battery_low_cmd = notify-send "battery low"
bat1_font = sans 7
bat2_font = sans 7
battery_font_color = #ffffff 76
battery_padding = 1 0
battery_background_id = 0

#---------------------------------------------
# TOOLTIP
#---------------------------------------------
tooltip = 0
tooltip_padding = 2 2
tooltip_show_timeout = 0.7
tooltip_hide_timeout = 0.3
tooltip_background_id = 0
tooltip_font_color = #OOOOOO 80
tooltip_font = sans 6

#---------------------------------------------
# MOUSE ACTION ON TASK
#---------------------------------------------
mouse_middle = none
mouse_right = close
mouse_scroll_up = none
mouse_scroll_down = none
```

It *seems* like Openbox is expecting the tray to be at the top of the screen. When I log in/out, the tray briefly flashes at the top of the screen, then returns to the bottom - where I want it. So, it's not truly transparent; Openbox (or tint2, I'm not sure which) is just poking a piece of the image behind the tray where it *thinks* the tray should be.

I think Openbox might just be having problems with transparency. I've set terminator's config to transparent as well. When I drag the terminator window across the desktop, the background image doesn't adjust until I drop it. Likewise, if I open terminator in front of other open windows, it shows the background image, not what's behind it. That's a "transparency = false" issue with terminator config, I know, but setting "transparency = true" results in an opaque terminator background. *shrug* Go figure.

So. Weird behavior with openbox/tint2. Any chance y'all have some ideas about fixing it?

---

### Post by MooPi on 2010-01-01
What app are you using to display your desktop. Nitrogen, feh ?Your wall paper maybe set to tiled and needs to be either scaled or centered possibly. Just taking a wild shot .
Cool desktop though. You wouldn't possibly be named Dave as well.

---

### Post by mailman1175 on 2010-01-02
> **MooPi said:**
> What app are you using to display your desktop. Nitrogen, feh ?Your wall paper maybe set to tiled and needs to be either scaled or centered possibly. Just taking a wild shot .
Cool desktop though. You wouldn't possibly be named Dave as well.
I'm using feh to set the desktop, and it's already centered. Weird stuff. And no, I'm not a Dave; just thought it was cool.

Thanks!
jeff

---

