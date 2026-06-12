---
title: "Conky Colorize Script"
date: 2010-05-13
forum: Desktop Environments
---

### Post by KrispyKritter on 2010-05-13
I have been bumping up against a wall for a couple of days now.

This is my .conkyrc file:

# Conky sample configuration
#
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check [http://conky.sf.net](http://conky.sf.net) for an up-to-date-list.
# set to yes if you want Conky to be forked in the background
background no
# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*
#font DejaVu Sans:size=8
# Use Xft?
use_xft yes
# Xft font when Xft is enabled
xftfont DejaVu Sans:size=8
# Text alpha when using Xft
xftalpha 0.8
# Print everything to stdout?
# out_to_console no
# MPD host/port
# mpd_host localhost
# mpd_port 6600
# mpd_password tinker_bell
# Print everything to console?
# out_to_console no
# mail spool
#mail_spool $MAIL
# Update interval in seconds
update_interval 3.0
# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0
# Create own window instead of using desktop (required in nautilus)
own_window yes
# If own_window is yes, you may use type normal, desktop or override
own_window_type override
# Use pseudo transparency with own_window?
own_window_transparent yes
# If own_window_transparent is set to no, you can set the background colour    here
own_window_colour hotpink
# If own_window is yes, these window manager hints may be used
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_hints undecorated,below,sticky
# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes
# Minimum size of text area
minimum_size 280 5
# Draw shades?
draw_shades no
# Draw outlines?
draw_outline no
# Draw borders around text
draw_borders no

# Draw borders around graphs
  draw_graph_borders yes

# Stippled borders?
  stippled_borders 8

# border width
  border_width 1

# Default colors and also border colors
  default_color black
  default_shade_color black
  default_outline_color black
color2 red
color4 yellow
color5 green

# Text alignment, other possible values are commented
 #alignment top_left
  alignment top_right
 #alignment bottom_left
 #alignment bottom_right
 #alignment none

# Gap between borders of screen and text

# same thing as passing -x at command line
  gap_x 12
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

# Add spaces to keep things from moving about? This only affects certain objects.
  use_spacer none

# Allow each port monitor to track at most this many connections (if 0 or not set, default is 256)
 #max_port_monitor_connections 256
# Maximum number of special things, e.g. fonts, offsets, aligns, etc.
 #max_specials 512
# Maximum size of buffer for user text, i.e. below TEXT line.
 #max_user_text 16384
# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument
# stuff after 'TEXT' will be formatted on screen

TEXT
${color blue}${font DejaVu Sans:bold:size=10}SYSTEM ${hr 2}$color $font
$color $nodename - $sysname $kernel on $machine
${color blue}${font DejaVu Sans:bold:size=10}CPU ${hr 2}$color $font
Uptime:${color blue} $uptime $color 
${color}Avg CPU Usage: ${color blue} $cpu% ${color}${alignr}CPU Temp:${color5}${execi 8 sensors | grep -A 1 'temp1:' | cut -c14-18| sed '/^$/d'}°C $color
[COLOR=Red]Temp: ${execi 8 sensors | grep -A 1 'temp1:' | cut -c15-16 | sed '/^$/d' | ~/ConkyScripts/CPUTempColorize.sh }°C $color[/COLOR]
${color red}${cpubar}
${color #606060}${cpugraph 42AE4A 0000ff}
${color}Usage (Core 0): ${color #0000ff}${freq cpu1}MHZ (${cpu cpu1}%) ${color red}${cpubar cpu1}
${color #606060}${cpugraph cpu1 42AE4A 0000ff}
${color}Usage (Core 1): ${color #0000ff}${freq cpu2}MHZ (${cpu cpu2}%) ${color red}${cpubar cpu2}
${color #606060}${cpugraph cpu2 42AE4A 0000ff} 
${color blue}${font DejaVu Sans:bold:size=10}Temperatures ${hr 2}$color $font

#${color}CPU Temp:${color blue} ${execi 1100 cat /proc/acpi/thermal_zone/THRM/temperature | grep -o "[0-9]* C"}
${color}Core 1 Junction Temp: ${color blue}${execi 8 sensors | grep -m 1 'Core0' | cut -c13-16 | sed '/^$/d'} C ${color}
#${color}Core 1 Case Temp: ${color blue}${execi 8 sensors | grep -m 2 'Core0' | cut -c13-16 | sed '/^$/d'} C ${color}
${color}Core 2 Temp: ${color blue}${execi 8 sensors | grep 'Core1' -m 1 | cut -c13-16 | sed '/^$/d'} C
$color$hr
${color}Processes:${color blue} $processes ${color}Run:${color blue} $running_processes 
${color}RAM Usage:${color #0000ff} $mem/$memmax  ${color #000000}$memperc% ${color2}${membar}
#$color Swap Usage:${color #606060} $swap/$swapmax - $swapperc% ${swapbar}
$color$hr
Networking:
${addr wlan0}
               Down:                                         Up:
${color blue}${font DejaVu Sans Mono:size=8}${downspeed wlan0}/s$alignr${upspeed wlan0}/s $font $color
${color blue}${downspeedgraph wlan0 32,150 ff0000 0000ec} ${upspeedgraph wlan0    32,150 0000ff ec0000}
$color File systems: / ${color blue}${fs_free /}(${fs_free_perc /}%)${color red} ${fs_bar /}$color

$color}Name${alignr 45}PID         CPU%      MEM%
${color red}${top name 1}${font DejaVu Sans Mono:size=8}${alignr 40}${top pid 1}   ${top cpu 1}   ${top mem 1}$color $font
${color blue}${top name 2}${font DejaVu Sans Mono:size=8}${alignr 40}${top pid 2}   ${top cpu 2}   ${top mem 2}$color $font
${color blue}${top name 3}${font DejaVu Sans Mono:size=8}${alignr 40}${top pid 3}   ${top cpu 3}   ${top mem 3}$color $font
${color blue}${top name 4}${font DejaVu Sans Mono:size=8}${alignr 40}${top pid 4}   ${top cpu 4}   ${top mem 4}$color $font
$color$hr

The red line returns:
[COLOR=Red]${color5}[/COLOR] instead of the temperature in green.

This is my CPUTempColorize.sh file:

!/bin/bash
# colorize.sh
# by Crinos512
# Usage:
#  ${execpi 6 sensors | grep 'Core 0' | paste -s | cut -c15-18 | xargs ~/.conky/conkyparts/colorize.sh} ... $color
# or
#  ${execpi 6 sensors | grep 'Core 0' | paste -s |sed 's/°/\n/'| head -n1 | cut -c15- | xargs ~/.conky/conkyparts/colorize.sh} ... $color
#
# Note: Assign color5, color4, and color2 to GOOD, CAUT, and WARN respectively
#   your .conkyrc
 
GOOD=50
CAUT=55
 
if [[ $1 -lt $GOOD ]]
   then echo "\${color5}"$1    # Good
elif [[ $1 -gt $CAUT ]]
   then echo "\${color2}"$1    # Danger
else echo "\${color4}"$1       # Caution
fi
 
exit 0

I must have missed paying my syntax somewhere:rolleyes:

---

### Post by 2hot6ft2 on 2010-05-13
> **KrispyKritter said:**
> 
TEXT
${color blue}${font DejaVu Sans:bold:size=10}SYSTEM ${hr 2}[COLOR="DarkRed"]$color $font[/COLOR]
[COLOR="DarkRed"]$color $nodename - $sysname $kernel on $machine[/COLOR]
${color blue}${font DejaVu Sans:bold:size=10}CPU ${hr 2}[COLOR="DarkRed"]$color $font[/COLOR]
Uptime:${color blue} $uptime $color 
${color}Avg CPU Usage: ${color blue} $cpu% ${color}${alignr}CPU Temp:${color5}${execi 8 sensors | grep -A 1 'temp1:' | cut -c14-18| sed '/^$/d'}°C $color
[COLOR=Red]Temp: ${execi 8 sensors | grep -A 1 'temp1:' | cut -c15-16 | sed '/^$/d' | ~/ConkyScripts/CPUTempColorize.sh }°C [COLOR="DarkRed"]$color[/COLOR][/COLOR]
${color red}${cpubar}
${color #606060}${cpugraph 42AE4A 0000ff}
${color}Usage (Core 0): ${color #0000ff}${freq cpu1}MHZ (${cpu cpu1}%) ${color red}${cpubar cpu1}
${color #606060}${cpugraph cpu1 42AE4A 0000ff}
${color}Usage (Core 1): ${color #0000ff}${freq cpu2}MHZ (${cpu cpu2}%) ${color red}${cpubar cpu2}
${color #606060}${cpugraph cpu2 42AE4A 0000ff} 
${color blue}${font DejaVu Sans:bold:size=10}Temperatures ${hr 2}[COLOR="DarkRed"]$color $font[/COLOR]

#${color}CPU Temp:${color blue} ${execi 1100 cat /proc/acpi/thermal_zone/THRM/temperature | grep -o "[0-9]* C"}
${color}Core 1 Junction Temp: ${color blue}${execi 8 sensors | grep -m 1 'Core0' | cut -c13-16 | sed '/^$/d'} C ${color}
#${color}Core 1 Case Temp: ${color blue}${execi 8 sensors | grep -m 2 'Core0' | cut -c13-16 | sed '/^$/d'} C ${color}
${color}Core 2 Temp: ${color blue}${execi 8 sensors | grep 'Core1' -m 1 | cut -c13-16 | sed '/^$/d'} C
$color$hr
${color}Processes:${color blue} $processes ${color}Run:${color blue} $running_processes 
${color}RAM Usage:${color #0000ff} $mem/$memmax  ${color #000000}$memperc% ${color2}${membar}
#[COLOR="DarkRed"]$co[/COLOR]lor Swap Usage:${color #606060} $swap/$swapmax - $swapperc% ${swapbar}
[COLOR="DarkRed"]$color$hr[/COLOR]
Networking:
${addr wlan0}
               Down:                                         Up:
${color blue}${font DejaVu Sans Mono:size=8}${downspeed wlan0}/s$alignr${upspeed wlan0}/s $font $color
${color blue}${downspeedgraph wlan0 32,150 ff0000 0000ec} ${upspeedgraph wlan0    32,150 0000ff ec0000}
$color File systems: / ${color blue}${fs_free /}(${fs_free_perc /}%)${color red} ${fs_bar /}$color

[COLOR="DarkRed"]$co[/COLOR]lor}Name${alignr 45}PID         CPU%      MEM%
${color red}${top name 1}${font DejaVu Sans Mono:size=8}${alignr 40}${top pid 1}   ${top cpu 1}   ${top mem 1}[COLOR="DarkRed"]$color $font[/COLOR]
${color blue}${top name 2}${font DejaVu Sans Mono:size=8}${alignr 40}${top pid 2}   ${top cpu 2}   ${top mem 2}[COLOR="DarkRed"][COLOR="DarkRed"]$color $font[/COLOR][/COLOR]
${color blue}${top name 3}${font DejaVu Sans Mono:size=8}${alignr 40}${top pid 3}   ${top cpu 3}   ${top mem 3}[COLOR="DarkRed"][COLOR="DarkRed"]$color $font[/COLOR][/COLOR]
${color blue}${top name 4}${font DejaVu Sans Mono:size=8}${alignr 40}${top pid 4}   ${top cpu 4}   ${top mem 4}[COLOR="DarkRed"][COLOR="DarkRed"]$color $font[/COLOR][/COLOR]
$color$hr

The red line returns:
[COLOR=Red]${color5}[/COLOR] instead of the temperature in green.

This is my CPUTempColorize.sh file:

!/bin/bash
# colorize.sh
# by Crinos512
# Usage:
#  ${execpi 6 sensors | grep 'Core 0' | paste -s | cut -c15-18 | xargs ~/.conky/conkyparts/colorize.sh} ... $color
# or
#  ${execpi 6 sensors | grep 'Core 0' | paste -s |sed 's/°/\n/'| head -n1 | cut -c15- | xargs ~/.conky/conkyparts/colorize.sh} ... [COLOR="DarkRed"]$color[/COLOR]
#
# Note: Assign color5, color4, and color2 to GOOD, CAUT, and WARN respectively
#   your .conkyrc
 
GOOD=50
CAUT=55
 
if [[ $1 -lt $GOOD ]]
   then echo "\${color5}"$1    # Good
elif [[ $1 -gt $CAUT ]]
   then echo "\${color2}"$1    # Danger
else echo "\${color4}"$1       # Caution
fi
 
exit 0

I must have missed paying my syntax somewhere:rolleyes:
Where are all the {} brackets around color and font?
There are too many to highlight them all but you get the idea.
You might do a search for conky gui and install it. It might help with your syntax.

---

### Post by KrispyKritter on 2010-05-13
> **2hot6ft2 said:**
> Where are all the {} brackets around color and font?
There are too many to highlight them all but you get the idea.
You might do a search for conky gui and install it. It might help with your syntax.

From my understanding If there is not a value change the {} are not required. IE $color = ${color}, changes the color back to the default color.  Everything in the script is working except the line that calls the script.  The value that I am getting back is the samething that the script returns when it is run in a terminal window.

---

### Post by KrispyKritter on 2010-05-14
It is not possible to pass a conky variable to a script and then get the variable back.

The "df" command had to be used.  The following line is inserted into the conkyrc file
[COLOR=Red]${execpi 6 df / | tail -n1 | awk '{ print $5}'| sed 's/%//' | xargs /ConkyScripts/DiskUsageColorize.sh}$color%[/COLOR]

 This is the script file to do the color change of the value:  
===================================================
# colorize.sh
# by Crinos512
# Usage:
#  ${execpi 6 sensors | grep 'Core 0' | paste -s | cut -c15-18 | xargs ~/.conky/conkyparts/colorize.sh} ... $color
# or
#  ${execpi 6 sensors | grep 'Core 0' | paste -s |sed 's/°/\n/'| head -n1 | cut -c15- | xargs ~/.conky/conkyparts/colorize.sh} ... $color
#
# Note: Assign color5=Green (GOOD), color4=Yellow (CAUT), and color2=Red (WARN) respectively
#   your .conkyrc
NUM1=100  # 100 Percent
GOOD=50
CAUT=10

PF=$(($NUM1 - $1)) # Calcuates Percentage of Free Disk Space
 
if [[ $PF -le $CAUT ]]
   then echo "\${color2}"$PF    # Good
elif [[ $PF -le $GOOD ]]
   then echo "\${color4}"$PF    # Danger
else echo "\${color5}"$PF       # Caution
fi

exit 0
=======================================
NOTE: "df" returns amount of disk space used not anount free.  Also this is running on MEPIS so the directory calls are slightly different.

Thanks to Crinos512

---

