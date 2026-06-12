---
title: "Tint2 Maximize Over and Gedit"
date: 2008-12-11
forum: General Help
---

### Post by easybake on 2008-12-11
I just started using tint2 on fluxbox. I wanted to know if there is a way to make windows maximize over the panel. I've tried looking at the documentation but I didn't see anything.

Also Gedit doesn't appear in the window list. Every other program does but not gedit.

Any idea on how to fix this?
```
#---------------------------------------------
# TINT CONFIG FILE
#---------------------------------------------

#---------------------------------------------
# PANEL
#---------------------------------------------
panel_mode = single_monitor
panel_monitor = 1
panel_position = bottom center
panel_size = 750 28
panel_margin = 15 0
panel_padding = 9 3
font_shadow = 0

#---------------------------------------------
# PANEL BACKGROUND AND BORDER
#---------------------------------------------
panel_rounded = 7
panel_border_width = 1
panel_background_color = #000000 60
panel_border_color = #ffffff 18

#---------------------------------------------
# TASKS
#---------------------------------------------
task_text_centered = 1
task_width = 120
task_margin = 2
task_padding = 6
task_icon_size = 13
task_font = sans 7
task_font_color = #ffffff 70
task_active_font_color = #ffffff 85

#---------------------------------------------
# TASK BACKGROUND AND BORDER
#---------------------------------------------
task_rounded = 5
task_background_color = #ffffff 30
task_active_background_color = #ffffff 50
task_border_width = 0
task_border_color = #ffffff 18
task_active_border_color = #ffffff 70

#---------------------------------------------
# CLOCK
#---------------------------------------------
time1_format = %H:%M
time1_font = sans 8
time2_format = %A %d %B
time2_font = sans 6
clock_font_color = #ffffff 76

#---------------------------------------------
# MOUSE ACTION ON TASK
#---------------------------------------------
mouse_middle = none
mouse_right = close
mouse_scroll_up = toggle
mouse_scroll_down = iconify

```

---

### Post by easybake on 2008-12-14
Anyone have any ideas why Gedit wouldn't appear in the tint panel? I've ran an update but still no luck.

---

### Post by Kilcros on 2009-09-09
Hi, everybody. Sorry to bring up an old thread but this page seems to be top of the list for google searches for people looking for a way to maximize windows over tint2.

I grabbed the code for the most recent version of tint2 (0.7.1) and modified it to allow an additional option in the tint2rc file. Voila - Lots of happy people able to maximize windows over their panel.

Here's the source: [http://www.mediafire.com/?mjmmyoz2yy0](http://www.mediafire.com/?mjmmyoz2yy0)

If you add the line "reserve_space = 0" or, if the "reserve_space" setting isn't present in your tint2rc file, then the panel will allow windows to maximize over it. Setting "reserve_space" to 1 will make tint2 act like normal, reserving space as usual. The default tint2rc file I packed in with the source has "reserve_space = 1" set.

Hope this helps anyone who's been looking for a way to do this.

---

