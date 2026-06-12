---
title: "conky and KDE4?"
date: 2008-02-13
forum: Desktop Environments
---

### Post by xelapond on 2008-02-13
I just installed KDE4 and conky.  I have never used conky before, but I looked at [this]("http://ubuntuforums.org/showthread.php?t=281865&highlight=conky") thread to find one I liked.  I found one, and in the screenshot it has a clear background, they have it running in gnome.  When I run it in KDE4 it has an ugly blue background.

Here is my conkyrc:

```
# set to yes if you want Conky to be forked in the background
background no

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-35-*-*-*-*-*-*-*

# Use Xft?
use_xft no

# Set conky on the bottom of all other applications
#on_bottom yes

# Xft font when Xft is enabled
#xftfont Bitstream Vera Sans Mono:size=10

# Text alpha when using Xft
#xftalpha 0.15

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
update_interval 5.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes

# If own_window is yes, you may use type normal, desktop or overide
own_window_type normal

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window_transparent is set to no, you can set the background colour here
#own_window_colour

# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer no

# Minimum size of text area
minimum_size 280 5

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 8 no

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color black

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 12
gap_y 28

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
override_utf8_locale no


# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer no

#   mldonkey_hostname     Hostname for mldonkey stuff, defaults to localhost
#   mldonkey_port         Mldonkey port, 4001 default
#   mldonkey_login        Mldonkey login, default none
#   mldonkey_password     Mldonkey password, default none

# boinc (seti) dir
# seti_dir /opt/seti

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT
           $sysname $kernel on $machine

${color}Uptime:$color $uptime ${color}- Load:$color $loadavg
${color}CPU Usage:${color} $cpu% ${cpubar}
${color}${cpugraph 88aadd 88aaee}

${color}RAM Usage:$color $mem/$memmax - $memperc% ${membar}
${color}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar}
${color}Processes:$color $processes  ${color}Running:$color $running_processes

${color}Networking:
 Down:${color} ${downspeed eth0} k/s${color} ${offset 80}Up:${color} ${upspeed eth0} k/s
${color}${downspeedgraph eth0 32,150 88aadd 88aaee} ${color}${upspeedgraph eth0 32,150 88aadd 88aaee}

${color}File systems:
 / $color${fs_used /}/${fs_size /} ${fs_bar /}
 /home $color${fs_used /home}/${fs_size /home} ${fs_bar /home}

${color}Name              PID     CPU%   MEM%
${color lightgrey} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}
${color}Mem usage
${color lightgrey} ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color} ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color} ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}
```

Is there any way to make it transparent?

Thanks, 

Alex

---

### Post by mojoman on 2008-02-15
I would tamper with some settings. My first suspect would be:
```

# If own_window is yes, you may use type normal, desktop or overide
own_window_type normal
```

Try the other alternatives, such as:
```
# If own_window is yes, you may use type normal, desktop or overide
own_window_type desktop
```

If that doesn't work, I'd go for the override alternative. Trial and error is usually the way to go in these situations.

Also, when I tweak my conky I always start it from the terminal (just type conky) and I don't run it in the background. It starts up and I can see what my changes caused. I then shut it down by pressing ctrl+c thus ending the active command in the terminal. I open the .conkyrc again, tweak some more, save the changes and start conky again. I usually end up repeating this process a million times before I got it just the way I like it. 

This _[page]("http://conky.sourceforge.net/config_settings.html")_ will explain all conky file settings.

---

