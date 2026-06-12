---
title: "CPU Frequency Scaling on KDE"
date: 2008-12-23
forum: Desktop Environments
---

### Post by Mewshi on 2008-12-23
Is there anything like the CPU Frequency Scaling applet (from GNOME) for KDE 4?

Thanks!

---

### Post by MarblePanther on 2008-12-23
Yep, just right click on the battery icon in the tray and highlight cpu policy.

---

### Post by Mewshi on 2008-12-23
I don't have a battery icon in my system tray :(  Do I need to install something for it?

---

### Post by MarblePanther on 2008-12-23
go into synaptic and install guidance-power-manager
(you should already have it on a default install)

---

### Post by Mewshi on 2008-12-23
That isn't all I'm looking for though...
I want it to tell me what frequency the CPU cores are running at...
Also, when I set it to "powersave" it locks the screen until I put my password back in...

---

### Post by MarblePanther on 2008-12-23
Ahhh, I see.  Try this in your terminal:

cat /proc/cpuinfo

Oh, and just rest your cursor without clicking over the guidance applet and it will show you the frequency

---

### Post by Mewshi on 2008-12-23
Is there a way I can get it to show me that all the time?  That's *exactly* what I want!

---

### Post by MarblePanther on 2008-12-23
oops double post

---

### Post by MarblePanther on 2008-12-23
Yes, just install conky from synaptic.

It is a system monitor that stays on your desktop background.

Once you install it, create a file called .conkyrc (you need to check show hidden files) in your home folder.

And you need to add a configuration for it in this .conkyrc

This is what I use:

```
# -- CODYLD -- CONKY
# Check http://conky.sf.net for an up-to-date-list.

# set to yes if you want Conky to be forked in the background
background yes

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=8

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
mail_spool $MAIL

# Update interval in seconds
update_interval 3.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes

# If own_window is yes, you may use type normal, desktop or override
own_window_type normal

# Use pseudo transparency with own_window?
own_window_transparent no

# If own_window_transparent is set to no, you can set the background colour here
# own_window_colour black

# If own_window is yes, these window manager hints may be used
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_hints undecorated,below,skip_taskbar

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 280 5

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders yes

# Draw borders around graphs
draw_graph_borders yes

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 0

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
gap_x 0
gap_y 0

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
use_spacer none

# Allow each port monitor to track at most this many connections (if 0 or not set, default is 256)
#max_port_monitor_connections 256

# Maximum number of special things, e.g. fonts, offsets, aligns, etc.
#max_specials 512

# Maximum size of buffer for user text, i.e. below TEXT line.
#max_user_text 16384

# Timing interval for music player thread, e.g. mpd, audacious
#music_player_interval (update_interval is default)

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT
${color green}$nodename - ${color green}$sysname ${color green}$kernel on ${color green}$machine
${color lightgrey}Uptime:$color $uptime ${color lightgrey}- Load:$color $loadavg
${color lightgrey}CPU Usage:${color #cc2222} $cpu% ${cpubar}
${color lightgrey}CPU Temp:${color #cc2222} ${acpitemp}${color}c ${color red}${acpitempf}${color}f
${color lightgrey}RAM Usage:$color $mem/$memmax - $memperc% ${membar}
${color lightgrey}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar}
${color lightgrey}Processes:$color $processes  ${color grey}Running:$color $running_processes
${color lightgrey}File systems:
 / $color${fs_used /}/${fs_size /} ${fs_bar /}
${color #ddaa00}Port(s)${alignr}#Connections   
$color Inbound: ${tcp_portmon 1 32767 count}  Outbound: ${tcp_portmon 32768 61000 count}${alignr}ALL: ${tcp_portmon 1 65535 count}
```

Then add conky to your sessions startup.


EDIT: You'll have to research in google about displaying cpu frequency in conky.  I dont recall what the code for it is atm.





EDIT EDIT:







Ahhh, I just remembered, a month from now when kde 4.2 is released there will be a widget included that will display your cpu frequency

---

### Post by Mewshi on 2008-12-23
No, I want something *in* the system tray to do this.  Not a separate program that I need to manually check every so often :\

---

### Post by MarblePanther on 2008-12-23
I already mentioned just mouse over the guidance power manager in the tray and it will show you
[ATTACH]97370[/ATTACH]

Also conky sits on your desktop from startup and stays there, but you'll have to research the code in the script for it to display cpu frequency

Also I mentioned when 4.2 comes out there will be a cpu monitoring widget for your desktop

---

### Post by Mewshi on 2008-12-23
Actually, I want it to display it in the bar the whole time... no way to do this?

---

### Post by MarblePanther on 2008-12-23
I'm not aware of anything like that in kde4 as of right now

The widget in upcoming 4.2 can dock in the panel

So just wait a month

---

### Post by Mewshi on 2008-12-23
K, cap'n.

Thanks for your help!

---

