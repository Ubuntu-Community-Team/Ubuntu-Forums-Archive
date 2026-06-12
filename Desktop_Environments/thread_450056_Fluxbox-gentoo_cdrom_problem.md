---
title: "Fluxbox-gentoo cdrom problem"
date: 2007-05-20
forum: Desktop Environments
---

### Post by thegrimgod on 2007-05-20
My bro installed gentoo with fluxbox cause he bragged gentoo has low system req , i wanted fluxbox(that was my pick). My problem now is that in my cdrom, besides the fact that i have to mount it, and i cant eject it, dont know y it always is busy, it is limited to the 8 character thing...meaning battlenet folder only shows battlene so i cant install warcraft :(  , now if anybody has any sol it would be great
Moreover , can anybody recommend me a way to customize ubuntu for low harware , like a server install , i have no clue how to do it, but i want fluxbox over it, im not gona put fluxbuntu , tried it...sigh..., in any case thx in advance , later

---

### Post by kerry_s on 2007-05-21
Grab the server net installer-> [http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso](http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso)
burn and boot the cd
then type server to do the server install, don't select a setup, you want bare bones.
login
sudo su
apt-get install xorg gdm synaptic fluxbox
reboot
choose fluxbox from the session menu and login
open synaptic and install what ever else you want.
Good luck.

---

### Post by thegrimgod on 2007-05-27
Well mate did as u said , now im working on making the system run smooth and nice , and look pretty :P 
First issue : when i boot up i get this error shpc_init: cannot reserve MMIO region
Don't know what it is , but i dont like it :( 
Second thing that i get is the login mannager saying it cant find the human theme , maybe because it aint there..who knows, but how do i solve/make the error go away.
Third , apparently my menu cant include png as icons, i know i had this issue in gentoo too  , and after recompiling fluxbox with IMLIB flag i believe it worked , how do i do it here...there i would just do emerge USE="IMLIB" fluxbox, i believe , again im not really on this planet most of the time ..srry :(
Now i need sugestions: what kind of file mannager would u recommend, again i need something that is good , but low on res, and a system manager or something like that ,that gives u specs about ur system, i heard about conky or torsmo or something like that , need sugesstions
Thx 
Night all

---

### Post by kerry_s on 2007-05-27
> **thegrimgod said:**
> Well mate did as u said , now im working on making the system run smooth and nice , and look pretty :P 
First issue : when i boot up i get this error shpc_init: cannot reserve MMIO region
Don't know what it is , but i dont like it :( 
Second thing that i get is the login mannager saying it cant find the human theme , maybe because it aint there..who knows, but how do i solve/make the error go away.
Third , apparently my menu cant include png as icons, i know i had this issue in gentoo too  , and after recompiling fluxbox with IMLIB flag i believe it worked , how do i do it here...there i would just do emerge USE="IMLIB" fluxbox, i believe , again im not really on this planet most of the time ..srry :(
Now i need sugestions: what kind of file mannager would u recommend, again i need something that is good , but low on res, and a system manager or something like that ,that gives u specs about ur system, i heard about conky or torsmo or something like that , need sugesstions
Thx 
Night all

I don't know about the shpc_init error, is it causing problems at boot?
To fix the login manger theme error, go into the gdmsetup and select one of the themes that's there, you can also setup the auto login if you want to skip the login altogether.
I have no clue on the png i don't use icons.
I just use plain old emelfm for my filemanager, but if your the icon type go for thunar.
I use conky on all my systems for the monitor.

```
# Conky sample configuration
#
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check http://conky.sf.net for an up-to-date-list.

# set to yes if you want Conky to be forked in the background
background true

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
font -*-*-*-*-*-*-80-*-*-*-*-*-*-*


# Use Xft?
use_xft yes

# Set conky on the bottom of all other applications
own_window_hints below

# Xft font when Xft is enabled
xftfont Sans-Serif:size=8

# Text alpha when using Xft
xftalpha 1

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
own_window true
own_window_type override
own_window_hints undecorated,skip_taskbar,skip_pager

# Use pseudo transparency with own_window?
own_window_transparent true

# If own_window_transparent is set to no, you can set the background colour here
#own_window_colour hotpink

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

# Stippled borders?
stippled_borders 8

# border margins
border_margin 10

# border width
border_width 10

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
gap_x 10
gap_y 10

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 1

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 1

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no


# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer yes

#   mldonkey_hostname     Hostname for mldonkey stuff, defaults to localhost
#   mldonkey_port         Mldonkey port, 4001 default
#   mldonkey_login        Mldonkey login, default none
#   mldonkey_password     Mldonkey password, default none

# boinc (seti) dir
# seti_dir /opt/seti

# Allow for the creation of at least this number of port monitors (if 0 or not set, default is 16) 
#min_port_monitors 16

# Allow each port monitor to track at least this many connections (if 0 or not set, default is 256)
#min_port_monitor_connections 256

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

#${execi 300 fortune -a | fold -w50}

TEXT
${color white}              ${time %l:%M %a %b %d}
${hr}
CPU: ${freq_g}GHz / Clocked: ${freq_dyn}MHz / Temp: ${acpitemp}C 
Disk I/O:${diskio}    Uptime:$uptime 
Processes:$processes  Running:$running_processes
CPU Usage:$cpu% ${cpugraph  20, 125 ffffff 0000ff}

RAM Usage:$mem of $memmax - $memperc% 
Swap Usage:$swap of $swapmax - $swapperc% 
File systems: ${fs_used /} of ${fs_size /}

Name                     PID     CPU%   MEM%
${top name 1}         ${top pid 1} ${top cpu 1} ${top mem 1}
${top name 2}         ${top pid 2} ${top cpu 2} ${top mem 2}
${top name 3}         ${top pid 3} ${top cpu 3} ${top mem 3}
${top name 4}         ${top pid 4} ${top cpu 4} ${top mem 4}
${top name 5}         ${top pid 5} ${top cpu 5} ${top mem 5}

   IN:${downspeed eth0} k/s          OUT:${upspeed eth0} k/s 
${downspeedgraph eth0 20,125 ff0000 0000ff} ${upspeedgraph eth0 20,125 0000ff ff0000}

Connections: ${tcp_portmon 1 65535 count}
Netstat 
${execi 2 netstat -e -p -t | grep ESTABLISHED | cut -c45-68,80-86,102-140}
${hr}

```

---

### Post by thegrimgod on 2007-05-27
The shpc_init error aint causing anything as far as i can see , but i just wanted to know what its all about , y is it there :P
In any case , thx for the fast reply , and essp for the conky sample config , very usefull, ill get into it tmrw , and post my results , to tired now , and ill check the FM u recommened
When i solve the png problem , ill post , maybe help others :)

---

### Post by RedSquirrel on 2007-09-09
OK, this is a rather old thread, but I came across it while looking for something else.  For PNG icons in the menu, you need to build Fluxbox from source and enable imlib2 support. 

```
./configure --enable-imlib2
```

(The configure script for the SVN version of Fluxbox currently enables imlib2 by default, which is kind of nice. :))

---

