---
title: "conky 1.3.1 still flickers"
date: 2005-11-25
forum: Desktop Environments
---

### Post by iced-tux on 2005-11-25
Hi everyone,
though I read a lot of thread, googled my a** off and searched the *extensive* thread at forums.gentoo.org, I couldn't figure out why my conky doesn't stop to flicker :(

I ```
aptitude install conky
``` 
this is my ~/.conkyrc:
```
# Conky sample configuration
#
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check http://conky.sf.net for an up-to-date-list.

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

# Use Xft?
use_xft no

# Set conky on the bottom of all other applications
on_bottom yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=10

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
update_interval 0.5

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window no


# Use pseudo transparency with own_window?
own_window_transparent no

# If own_window_transparent is set to no, you can set the background colour here
own_window_colour hotpink

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 280 5

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline yes

# Draw borders around text
draw_borders yes

# Stippled borders?
stippled_borders 8

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
alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 12
gap_y 12

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
$nodename - $sysname $kernel on $machine
$stippled_hr
${color lightgrey}Uptime:$color $uptime ${color lightgrey}- Load:$color $loadavg
${color lightgrey}CPU Usage:${color #cc2222} $cpu% ${cpubar}
${color red}${cpugraph 0000ff 00ff00}
${color lightgrey}RAM Usage:$color $mem/$memmax - $memperc% ${membar}
${color lightgrey}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar}
${color lightgrey}Processes:$color $processes  ${color grey}Running:$color $running_processes
$color$stippled_hr
${color lightgrey}Networking:
 Down:${color #8844ee} ${downspeed eth0} k/s${color lightgrey} ${offset 80}Up:${color #22ccff} ${upspeed eth0} k/s
${color #0000ff}${downspeedgraph eth0 32,150 ff0000 0000ff} ${color #22ccff}${upspeedgraph eth0 32,150 0000ff ff0000}
${color lightgrey}File systems:
 / $color${fs_used /}/${fs_size /} ${fs_bar /}
${color #ddaa00} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color lightgrey} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}
${color}Mem usage
${color #ddaa00} ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color lightgrey} ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color lightgrey} ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}

```

I have the the line
```
Load "dbe"
```
in my xorg.conf.

Anyone knows how to solve my problem ? :(

thanx 
iced-tux

---

### Post by taurus on 2005-11-25
I also have "dbe" (double buffer extension) in my /etc/X11/xorg.conf and my ~/.conkyrc looks similar to yours except I have it set to 1 second interval instead of 0.5 second and "double_buffer no" instead of "double_buffer yes" in your .conkyrc!  

So, set it to "no" for "double_buffer" in ~/.conkyrc and see what happens.  And by the way, is there any reason you want to set time interval to half a second instead of one second?

---

### Post by iced-tux on 2005-11-27
The option "double_buffer yes" is just to prevent the flickering *which it doesn't in my case*
The short intervall is just to keep a very sharp eye on my cpu.
BTW an intervall of 1 sec only makes it flickering every second instead 0.5 secs ;)

---

### Post by iced-tux on 2005-11-27
I just changed the setting to own_window_transparent yes
and now its working

---

