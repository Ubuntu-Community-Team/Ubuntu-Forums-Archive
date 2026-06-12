---
title: "Ubuntu 9.04 clean install with openbox3"
date: 2009-07-05
forum: Desktop Environments
---

### Post by cteam on 2009-07-05
I had been using xubuntu for quite some time and was unsatisfied with xfce and the general performance of my machine.  Im on a ASUS n50vn core 2 P8600 @ 2.4, 4gigs ddr2 ram, and a 9650m gt card to boot but im one of those paranoid computer users who always wants things to happen INSTANTLY with 0 slowdown, be extreemly light on ram and cpu.  With a fresh install of Ubuntu via the alternate_x64 install disk and this little guide [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems) i was on my feet.  

It is worth noting that durring the entire install process i was wired to the internet as wireless internet wont work untill you get a wireless manager, like WICD (great little manager)

The install went great, after following the basic instructions, and partitioning a ext4 section with a 2gb swap i installed the foundation of a graphic environment via command line:

sudo aptitude install openbox obconf openbox-themes xfe xfce4-terminal tango-icon-theme-extras xorg firefox thunar conky

this will give you the basics to just function normally.  btw conky is great, it is better than ANY google sidebar applet hahah what a joke.

From here i immediately installed the latest Nvidia drivers and picked up a little wireless network manager: WICD is great, lightweight, and supports WEP encryption. [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

After i got the essensials working i installed ambiword, vlc player, rtorrent, and wine with a n64 emu.

I was unsatisfied with the plain openbox look, even though i use keyboad shortcuts (which you can manage in your /home/.conf/openbox/xml file.), so i installed tint2 as a little dock and taskbar.  It is great, and i think is more lightweight than pypanel (which is also good.)  Setting up tint2 was tough for me because i dont know the hexadecimal color system, but i eventually got the colors i was looking for.  Setup is well documented here: [http://code.google.com/p/tint2/](http://code.google.com/p/tint2/)

If anyone is like me and wants their computer to be more responsive than it ever would under windows or even a normal buntu install... heck the only way you could do much better would be with arch linux... but i dont have that much linux experience and i was familiar with buntu anyway... Then you should go the alternate install + openbox3 way.

I run firefox, rtorrent, vlc w/music playing, and pidgin all the time, with a measly 4-5% of ram used and 2-6% cpu usage.  now THAT is efficent!



anyway lets get down to buisness here is my tint2rc and conkyrc and the obtheme i use:

obtheme:
[http://kiwisaotome.deviantart.com/art/Fall-is-Awesome-98169843](http://kiwisaotome.deviantart.com/art/Fall-is-Awesome-98169843)

conkyrc
```

# Conky, a system monitor, based on torsmo
#
# Any original torsmo code is licensed under the BSD license
#
# All code written since the fork of torsmo is licensed under the GPL
#
# Please see COPYING for details
#
# Copyright (c) 2004, Hannu Saransaari and Lauri Hakkarainen
# Copyright (c) 2005-2007 Brenden Matthews, Philip Kovacs, et. al. (see AUTHORS)
# All rights reserved.
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.
#
# $Id: conky.conf 1193 2008-06-21 20:37:58Z ngarofil $

# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048

# Update interval in seconds
update_interval 4

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_type normal
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 180 0
#maximum_width 200

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 5

# border width
border_width 1

# Default colors and also border colors
default_color grey
#default_shade_color black
#default_outline_color grey
own_window_colour grey

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 35
gap_y 35

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none

TEXT
SYSTEM ${hr 2}
${alignc 17}${font Arial Black:size=16}omns${font}
${alignc}smile, breathe and go slowly
Kernel:  ${alignr}${kernel}
Core 2 duo P8600 @ ${freq}MHz
CPU1: ${cpu cpu1}% ${alignr}${cpubar cpu1 8,60}
CPU2: ${cpu cpu2}% ${alignr}${cpubar cpu2 8,60}
RAM: $memperc% ${alignr}${membar 8,60}
Battery: ${battery_percent BAT0}% ${alignr}${battery_bar 8,60 BAT0}

DATE ${hr 2}
${alignc 17}${font Arial Black:size=16}${time %H:%M}${font}
${alignc}${time %A %d %B %Y}


NETWORK ${hr 2}
${if_existing /proc/net/route wlan0}
  Up: ${upspeed wlan0} kb/s ${alignr}${upspeedgraph wlan0 8,60 BEBEBE BEBEBE}
  Down: ${downspeed wlan0} kb/s ${alignr}${downspeedgraph wlan0 8,60 BEBEBE BEBEBE}
  Upload: ${alignr}${totalup wlan0}
  Download: ${alignr}${totaldown wlan0}
  Signal: ${wireless_link_qual wlan0}% ${alignr}${wireless_link_bar 8,60 wlan0}
Local Ip: ${alignr}${addr wlan0}
${else}${if_existing /proc/net/route eth0}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed eth0} kb/s ${alignr}${upspeedgraph eth0 8,60 789E2D A7CC5C}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed eth0} kb/s ${alignr}${downspeedgraph eth0 8,60 789E2D A7CC5C}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup eth0}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown eth0}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr eth0}
${endif}${else}${if_existing /proc/net/route eth1}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed eth1} kb/s ${alignr}${upspeedgraph eth1 8,60 789E2D A7CC5C}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed eth1} kb/s ${alignr}${downspeedgraph eth1 8,60 789E2D A7CC5C}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup eth1}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown eth1}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr eth1}
${endif}${else}
${font PizzaDude Bullets:size=14}4${font}   Network Unavailable
${endif}

PROCESSES ${hr 2}
NAME $alignr PID    CPU
${top name 1} $alignr ${top pid 1} ${top cpu 1}
${top name 2} $alignr ${top pid 2} ${top cpu 2}
${top name 3} $alignr ${top pid 3} ${top cpu 3}
${top name 4} $alignr ${top pid 4} ${top cpu 4}
${top name 5} $alignr ${top pid 5} ${top cpu 5}
${top name 6} $alignr ${top pid 6} ${top cpu 6}
${top name 7} $alignr ${top pid 7} ${top cpu 7}
${top name 8} $alignr ${top pid 8} ${top cpu 8}


${alignr}firefox windows + 1
${alignr}vlc windows + 2
${alignr}ambiword windows + 3
${alignr}pidgin windows + 4
```tint2rc
```

#---------------------------------------------
# TINT2 CONFIG FILE
#---------------------------------------------

#---------------------------------------------
# BACKGROUND AND BORDER
#---------------------------------------------
rounded = 7
border_width = 1
background_color = #000000 60
border_color = #ffffff 18

rounded = 0
border_width = 0
background_color = #7b3f00 70
border_color = #ffffff 18

rounded = 0
border_width = 0
background_color = #e3701a 95
border_color = #000000 70

rounded = 7
border_width = 1
background_color = #000000 60
border_color = #ffffff 18

rounded = 5
border_width = 0
background_color = #ffffff 30
border_color = #ffffff 18

rounded = 5
border_width = 0
background_color = #ffffff 50
border_color = #ffffff 70

#---------------------------------------------
# PANEL
#---------------------------------------------
panel_monitor = 1
panel_position = bottom left 
panel_size = 1200 34
panel_margin = 15 0
panel_padding = 9 3 9
font_shadow = 0
panel_background_id = 0
#wm_menu = 0

#---------------------------------------------
# TASKBAR
#---------------------------------------------
taskbar_mode = single_desktop
taskbar_padding = 5 2 5
taskbar_background_id = 0

#---------------------------------------------
# TASK
#---------------------------------------------
task_icon = 1
task_text = 1
task_size = 150
task_maximum_size = 150
task_centered = 1
task_padding = 6 4
task_font = sans 10
task_font_color = #ffffff 70
task_active_font_color = #7b3f00 100
task_background_id = 2
task_active_background_id = 3

#---------------------------------------------
# SYSTRAYBAR
#---------------------------------------------
# systray_padding = 4 3 4
# systray_background_id = 0

#---------------------------------------------
# CLOCK
#---------------------------------------------
#time1_format = %H:%M
time1_font = sans 8
#time2_format = %A %d %B
time2_font = sans 6
clock_font_color = #ffffff 76
clock_padding = 2 2
clock_background_id = 0
#clock_lclick_command = xclock
clock_rclick_command = orage

#---------------------------------------------
# BATTERY
#---------------------------------------------
battery = 0
battery_low_status = 0
battery_low_cmd = (null)
bat1_font = (null)
bat2_font = (null)
battery_font_color = #000000 0
battery_padding = 2 2
battery_background_id = 0

#---------------------------------------------
# MOUSE ACTION ON TASK
#---------------------------------------------
mouse_middle = none
mouse_right = close
mouse_scroll_up = toggle
mouse_scroll_down = iconify


```

---

### Post by ikisham on 2009-09-05
Great! I'm running a minimal Karmic+IceWm in a far older pc than yours and it's great too!
To get the hexadecimal codes for colors you may use [this]("http://www.colorpicker.com/")

---

### Post by cteam on 2009-10-19
thats a nice website :) thanks.

---

