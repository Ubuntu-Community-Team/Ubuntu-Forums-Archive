---
title: "Flickering Conky"
date: 2007-08-11
forum: Desktop Effects &amp; Customization
---

### Post by jeremy1138 on 2007-08-11
Hi I just installed Conky on my computer and it's working but I can't get it to stop flickering.  I have the double buffer in the .conkyrc file that I found somewhere else in this forum but it has an error when conky is started...

Here is my .conkyrc file:

```

# set to yes if you want Conky to be forked in the background
background no

cpu_avg_samples 2
net_avg_samples 2

out_to_console no

# X font when Xft is disabled, you can pick one with program xfontsel
#font 7x12
#font 6x10
#font 7x13
#font 8x13
#font 7x12
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*
#font -artwiz-snap-normal-r-normal-*-*-100-*-*-p-*-iso8859-1

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=8

own_window_transparent no
#own_window_colour hotpink
# Text alpha when using Xft
xftalpha 0.8

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 1
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_hints undecorated,below,skip_taskbar
own_window_type override

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 260 5
maximum_width 640

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders no

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color white
default_outline_color white

# Text alignment, other possible values are commented
#alignment top_left
#minimum_size 10 10
gap_x 10
gap_y 26
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text

# Add spaces to keep things from moving about? This only affects certain objects.
use_spacer no

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# boinc (seti) dir
# seti_dir /opt/seti

# Possible variables to be used:
#
# Variable Arguments Description
# acpiacadapter ACPI ac adapter state.
# acpifan ACPI fan state
# acpitemp ACPI temperature.
# adt746xcpu CPU temperature from therm_adt746x
# adt746xfan Fan speed from therm_adt746x
# battery (num) Remaining capasity in ACPI or APM
# battery. ACPI battery number can be
# given as argument (default is BAT0).
# buffers Amount of memory buffered
# cached Amount of memory cached
# color (color) Change drawing color to color
# cpu CPU usage in percents
# cpubar (height) Bar that shows CPU usage, height is
# bar's height in pixels
# downspeed net Download speed in kilobytes
# downspeedf net Download speed in kilobytes with one
# decimal
# exec shell command Executes a shell command and displays
# the output in torsmo. warning: this
# takes a lot more resources than other
# variables. I'd recommend coding wanted
# behaviour in C and posting a patch .
# execi interval, shell Same as exec but with specific interval.
# command Interval can't be less than
# update_interval in configuration.
# fs_bar (height), (fs) Bar that shows how much space is used on
# a file system. height is the height in
# pixels. fs is any file on that file
# system.
# fs_free (fs) Free space on a file system available
# for users.
# fs_free_perc (fs) Free percentage of space on a file
# system available for users.
# fs_size (fs) File system size
# fs_used (fs) File system used space
# hr (height) Horizontal line, height is the height in
# pixels
# i2c (dev), type, n I2C sensor from sysfs (Linux 2.6). dev
# may be omitted if you have only one I2C
# device. type is either in (or vol)
# meaning voltage, fan meaning fan or temp
# meaning temperature. n is number of the
# sensor. See /sys/bus/i2c/devices/ on
# your local computer.
# kernel Kernel version
# loadavg (1), (2), (3) System load average, 1 is for past 1
# minute, 2 for past 5 minutes and 3 for
# past 15 minutes.
# machine Machine, i686 for example
# mails Mail count in mail spool. You can use
# program like fetchmail to get mails from
# some server using your favourite
# protocol. See also new_mails.
# mem Amount of memory in use
# membar (height) Bar that shows amount of memory in use
# memmax Total amount of memory
# memperc Percentage of memory in use
# new_mails Unread mail count in mail spool.
# nodename Hostname
# outlinecolor (color) Change outline color
# pre_exec shell command Executes a shell command one time before
# torsmo displays anything and puts output
# as text.
# processes Total processes (sleeping and running)
# running_processes Running processes (not sleeping),
# requires Linux 2.6
# shadecolor (color) Change shading color
# stippled_hr (space), Stippled (dashed) horizontal line
# (height)
# swapbar (height) Bar that shows amount of swap in use
# swap Amount of swap in use
# swapmax Total amount of swap
# swapperc Percentage of swap in use
# sysname System name, Linux for example
# time (format) Local time, see man strftime to get more
# information about format
# totaldown net Total download, overflows at 4 GB on
# Linux with 32-bit arch and there doesn't
# seem to be a way to know how many times
# it has already done that before torsmo
# has started.
# totalup net Total upload, this one too, may overflow
# updates Number of updates (for debugging)
# upspeed net Upload speed in kilobytes
# upspeedf net Upload speed in kilobytes with one
# decimal
# uptime Uptime
# uptime_short Uptime in a shorter format
#
# seti_prog Seti@home current progress
# seti_progbar (height) Seti@home current progress bar
# seti_credit Seti@hoome total user credit


# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument
#${font Dungeon:style=Boldixelsize=10}I can change the font as well
#${font Verdana:size=10}as many times as I choose
#${font Perry:size=10}Including UTF-8,
# stuff after 'TEXT' will be formatted on screen
#${font Grunge:size=12}${time %a %b %d}${alignr -25}${time %k:%M}

TEXT
${color #0077ff}$sysname $kernel $machine - $nodename
${color #0077ff}Today is ${color lightgrey}${time %A, %d %B %Y}
${color #0077ff}The Time is ${color lightgrey}${time %H:%M.%S}${alignr}${color #0077ff}Uptime:${color lightgrey} $uptime

${color #0077ff}${execi 1000 cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'} ${color lightgrey}${freq_dyn}Mhz
${color #0077ff}Usage: ${color lightgrey}${cpu}% ${color #FCFF00}${cpubar}
${color #0077ff}${cpugraph 000000 FCFF00}
${color #0077ff}Processes:${color lightgrey} $processes ${color #0077ff}Run:${color lightgrey} $running_processes
${color #0077ff}CPU Usage PID CPU% MEM%
${color lightgrey} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color #0077ff} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color #0077ff} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}

${color #0077ff}RAM:${color lightgrey} $mem/$memmax - $memperc% ${alignr}${color #FF8E00}${membar 5,110}
${color #0077ff}SWP:${color lightgrey} $swap/$swapmax - $swapperc% ${alignr}${color #FF8E00}${swapbar 5,110}
${color #0077ff}Mem Usage
${color lightgrey} ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color #0077ff} ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color #0077ff} ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}

${color #0077ff}HD IO: ${color lightgrey}${diskio}
${color #0077ff}${diskiograph 000000 00EA01}
${color #0077ff}Hard Disks:
${color #0077ff} Root ${color lightgrey}${fs_used /}/${fs_size /}${alignr}${color #00EA01}${fs_bar 5,120 /}
${color #0077ff} Home ${color lightgrey}${fs_used /home}/${fs_size /home}${alignr}${color #00EA01}${fs_bar 5,120 /home}

${color #0077ff}Network: ${color lightgrey}${addr eth1}
${color #0077ff}Down:${color lightgrey} ${downspeed eth1} k/s $alignr${color #0077ff} Up:${color lightgrey} ${upspeed eth1} k/s
${color #0077ff}${downspeedgraph eth1 27,120 000000 FF0000 180} $alignr${color #0077ff}${upspeedgraph eth1 27,120 000000 FF0000 25}
${color lightgrey}${totaldown eth1} $alignr${color lightgrey}${totalup eth1}
${color #0077ff}Port(s)${offset 48}Connections:
${color #0077ff} ALL: ${color lightgrey}${alignc}${tcp_portmon 1 65535 count}
${color #0077ff} 1 - 1024:${color lightgrey}${alignc}${tcp_portmon 1 1024 count}
${color #0077ff} 1025 - 65535:${color lightgrey}${alignc}${tcp_portmon 1024 65535 count}

${color #0077ff}Remote Address:${alignr} Local Service/Port:
${color lightgrey}${tcp_portmon 1 1024 rport 0}
${color lightgrey}${tcp_portmon 1 65535 rhost 0}${alignr}${tcp_portmon 1 65535 lservice 0}
${color lightgrey}${tcp_portmon 1 65535 rhost 1}${alignr}${tcp_portmon 1 65535 lservice 1}
${color lightgrey}${tcp_portmon 1 65535 rhost 2}${alignr}${tcp_portmon 1 65535 lservice 2}
${color lightgrey}${tcp_portmon 1 65535 rhost 3}${alignr}${tcp_portmon 1 65535 lservice 3}
${color lightgrey}${tcp_portmon 1 65535 rhost 4}${alignr}${tcp_portmon 1 65535 lservice 4}
${color lightgrey}${tcp_portmon 1 65535 rhost 5}${alignr}${tcp_portmon 1 65535 lservice 5}
${color #0077ff}Fortune ${color #000000}${hr 2}
${color lightgrey}${execi 120 fortune -s | fold -w50}

```

And here is the error that I get in the terminal when I run conky.

```

jeremy@jeremy-laptop:~$ conky
Conky: desktop window (1000058) is subwindow of root window (56)
Conky: window type - override
Conky: drawing to created window (3600002)
Conky: failed to set up double buffer
Conky: drawing to single buffer

```

Does anyone have any ideas how I can fix this?  Thanks for your help!

---

### Post by jeremy1138 on 2007-08-12
No one has any idea?

---

### Post by siralphred on 2007-08-13
enable  dbe  in xorg.conf   i use nvidia  i did it by  adding  

Load          "dbe"      


 to the Extensions  section

---

### Post by kellemes on 2007-08-13
On the website of Conky you can find all info you need.

---

### Post by evilc on 2008-07-01
> **jeremy1138 said:**
> Hi I just installed Conky on my computer and it's working but I can't get it to stop flickering.  I have the double buffer in the .conkyrc file that I found somewhere else in this forum but it has an error when conky is started...



I had similar found that Fortune was the culprit, it's set for 50 wide but sometimes it's more, causing flicker to re-ajust. try removing it.

---

