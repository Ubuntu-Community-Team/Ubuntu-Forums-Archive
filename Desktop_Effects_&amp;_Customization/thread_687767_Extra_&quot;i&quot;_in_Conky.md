---
title: "Extra &quot;i&quot; in Conky"
date: 2008-02-04
forum: Desktop Effects &amp; Customization
---

### Post by MikeCheck on 2008-02-04
This may have been answered, but I couldn't find it anywhere.

For all of my memory and file system displays (mem, fs_used, ...) in conky, I am getting readings measured in "MiB" or "GiB".  Does anyone know how to get rid of that "i" character so that it just reads "MB" or "GB"?

Here is my conkyrc:
```
# conky configuration

# set to yes if you want Conky to be forked in the background
background yes

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*


# Use Xft?
use_xft yes

# Xft font when Xft is enabled
#xftfont Bitstream Vera Sans Mono:size=8
xftfont Terminus:size=9

# Text alpha when using Xft
xftalpha 0.8

# Print everything to console?
out_to_console no

# mail spool
#mail_spool $MAIL

# Update interval in seconds
update_interval 1.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_transparent yes

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 10

# border width
border_width 2

# Default colors and also border colors
default_color white
default_shade_color white
default_outline_color white

# Minimum size of text area
minimum_size 5 5
maximum_width 300

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 3
gap_y 75

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
use_spacer yes
#Note: doesn't work in conky 1.2 =(

TEXT
${color red}$nodename:
${color white}$sysname $kernel ${color #CCCCCC}on ${color white}$machine bit
IP:$alignr${addr eth0}
${color white}Uptime: $uptime
${color white}${time %a,}${time %e %B %G}$alignr${time %H:%M:%S}
${color white}${hr 2}

${color #ffccaa}System:
${color #00FF00}Core1: ${color white}${cpu cpu0}% $alignr${color white}${execi 2 cat /sys/bus/pci/drivers/k8temp/000*/temp1_input | cut -c1,2}°C
${color #00FF00}Core2: ${color white}${cpu cpu1}% $alignr${color white}${execi 2 cat /sys/bus/pci/drivers/k8temp/000*/temp3_input | cut -c1,2}°C
${color #00FF00}${cpugraph 25 ff0000 ff00ff}
${color #00FF00}RAM: ${color white}$mem${color #00FF00}/${color white}$memmax ${color #00FF00}, ${color white}$memperc%
${color #00FF00}swap: ${color white}$swap${color #00FF00}/${color white}$swapmax ${color #00FF00}, ${color white}$swapperc%
${color #00FF00}avg load: (${color white}$loadavg${color #00FF00})
${color #00FF00}processes: ${color white}$processes	${color #00FF00}running: ${color white}$running_processes
${color white}${hr 1}

${color #ffccaa}File Systems:
${color #00FF00}root: ${color white}${fs_used /}${color white}/${color white}${fs_size /} ${color white}(${color white}${fs_free /}, ${fs_free_perc /}% ${color white}free)
      ${color #888888} ${fs_bar /}
${color #00FF00}XP: ${color white}${fs_used /media/hda1}${color white}/${color white}${fs_size /media/hda1} ${color white}(${color white}${fs_free /media/hda1}, ${fs_free_perc /media/hda1}% ${color white}free)
       ${color #888888}${fs_bar /media/hda1}
${color #00FF00}Music: ${color white}${fs_used /media/hdb1}${color white}/${color white}${fs_size /media/hdb1} ${color white}(${color white}${fs_free /media/hdb1}, ${fs_free_perc /media/hdb1}% ${color white}free)
      ${color #888888} ${fs_bar /media/hdb1}
${color white}${hr 1}

${color #ffccaa}NET: 
${color #00ff00}Up: ${upspeed eth0} k/s     ${offset 66} Down: ${downspeed eth0}k/s
${upspeedgraph eth0 20,140 ff0000 ff00ff}   $alignr${downspeedgraph eth0 20,140 ff0000 ff00ff}
```

---

### Post by FuturePilot on 2008-02-04
There might be a way, but I'm not really sure. But it's not really an extra "i". MiB GiB etc. are the [NIST standard]("http://physics.nist.gov/cuu/Units/binary.html")
More info
[http://kerneltrap.org/node/340]("http://kerneltrap.org/node/340")
[http://bbs.archlinux.org/viewtopic.php?pid=247737]("http://bbs.archlinux.org/viewtopic.php?pid=247737")

---

