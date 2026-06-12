---
title: "Conky, not accept changes"
date: 2014-02-23
forum: Desktop Environments
---

### Post by pendulous on 2014-02-23
Installed conky and unable to get the script below to load. 

.conkyrc is in the home directy

killall -SIGUSR1 conky , to restart the app, but the default skin / location still displays.


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

on_bottom yes

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
maximum_width 260

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
gap_x 15
gap_y 70
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer no

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# none, xmms, bmp, audacious, infopipe (default is none)
xmms_player bmp

# boinc (seti) dir
# seti_dir /opt/seti

# Possible variables to be used:
#
#      Variable         Arguments                  Description                
#  acpiacadapter                     ACPI ac adapter state.                   
#  acpifan                           ACPI fan state                           
#  acpitemp                          ACPI temperature.                        
#  adt746xcpu                        CPU temperature from therm_adt746x       
#  adt746xfan                        Fan speed from therm_adt746x             
#  battery           (num)           Remaining capasity in ACPI or APM        
#                                    battery. ACPI battery number can be      
#                                    given as argument (default is BAT0).     
#  buffers                           Amount of memory buffered                
#  cached                            Amount of memory cached                  
#  color             (color)         Change drawing color to color            
#  cpu                               CPU usage in percents                    
#  cpubar            (height)        Bar that shows CPU usage, height is      
#                                    bar's height in pixels                   
#  downspeed         net             Download speed in kilobytes              
#  downspeedf        net             Download speed in kilobytes with one     
#                                    decimal                                  
#  exec              shell command   Executes a shell command and displays    
#                                    the output in torsmo. warning: this      
#                                    takes a lot more resources than other    
#                                    variables. I'd recommend coding wanted   
#                                    behaviour in C and posting a patch :-).  
#  execi             interval, shell Same as exec but with specific interval. 
#                    command         Interval can't be less than              
#                                    update_interval in configuration.        
#  fs_bar            (height), (fs)  Bar that shows how much space is used on 
#                                    a file system. height is the height in   
#                                    pixels. fs is any file on that file      
#                                    system.                                  
#  fs_free           (fs)            Free space on a file system available    
#                                    for users.                               
#  fs_free_perc      (fs)            Free percentage of space on a file       
#                                    system available for users.              
#  fs_size           (fs)            File system size                         
#  fs_used           (fs)            File system used space                   
#  hr                (height)        Horizontal line, height is the height in 
#                                    pixels                                   
#  i2c               (dev), type, n  I2C sensor from sysfs (Linux 2.6). dev   
#                                    may be omitted if you have only one I2C  
#                                    device. type is either in (or vol)       
#                                    meaning voltage, fan meaning fan or temp 
#                                    meaning temperature. n is number of the  
#                                    sensor. See /sys/bus/i2c/devices/ on     
#                                    your local computer.                     
#  kernel                            Kernel version                           
#  loadavg           (1), (2), (3)   System load average, 1 is for past 1     
#                                    minute, 2 for past 5 minutes and 3 for   
#                                    past 15 minutes.                         
#  machine                           Machine, i686 for example                
#  mails                             Mail count in mail spool. You can use    
#                                    program like fetchmail to get mails from 
#                                    some server using your favourite         
#                                    protocol. See also new_mails.            
#  mem                               Amount of memory in use                  
#  membar            (height)        Bar that shows amount of memory in use   
#  memmax                            Total amount of memory                   
#  memperc                           Percentage of memory in use              
#  new_mails                         Unread mail count in mail spool.         
#  nodename                          Hostname                                 
#  outlinecolor      (color)         Change outline color                     
#  pre_exec          shell command   Executes a shell command one time before 
#                                    torsmo displays anything and puts output 
#                                    as text.                                 
#  processes                         Total processes (sleeping and running)   
#  running_processes                 Running processes (not sleeping),        
#                                    requires Linux 2.6                       
#  shadecolor        (color)         Change shading color                     
#  stippled_hr       (space),        Stippled (dashed) horizontal line        
#                    (height)        
#  swapbar           (height)        Bar that shows amount of swap in use     
#  swap                              Amount of swap in use                    
#  swapmax                           Total amount of swap                     
#  swapperc                          Percentage of swap in use                
#  sysname                           System name, Linux for example           
#  time              (format)        Local time, see man strftime to get more 
#                                    information about format                 
#  totaldown         net             Total download, overflows at 4 GB on     
#                                    Linux with 32-bit arch and there doesn't 
#                                    seem to be a way to know how many times  
#                                    it has already done that before torsmo   
#                                    has started.                             
#  totalup           net             Total upload, this one too, may overflow 
#  updates                           Number of updates (for debugging)        
#  upspeed           net             Upload speed in kilobytes                
#  upspeedf          net             Upload speed in kilobytes with one       
#                                    decimal                                  
#  uptime                            Uptime                                   
#  uptime_short                      Uptime in a shorter format               
#
#  seti_prog                         Seti@home current progress
#  seti_progbar      (height)        Seti@home current progress bar
#  seti_credit                       Seti@hoome total user credit


# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument
#${font Dungeon:style=Bold:pixelsize=10}I can change the font as well
#${font Verdana:size=10}as many times as I choose
#${font Perry:size=10}Including UTF-8,
# stuff after 'TEXT' will be formatted on screen
#${font Grunge:size=12}${time %a  %b  %d}${alignr -25}${time %k:%M}

TEXT
${color #0077ff}$sysname $kernel $machine - $nodename 

${color #0077ff}Uptime:${color lightgrey} $uptime ${color #0077ff} Load:${color lightgrey} $loadavg

${color  #0077ff}${execi 1000 cat /proc/cpuinfo | grep 'model name' | sed -e  's/model name.*: //'} ${color lightgrey}${freq_dyn}Mhz
${color #0077ff}Usage:${color #0077ff} ${color lightgrey}${cpu}% ${color #0077ff}${cpubar}
${color #0077ff}${cpugraph 000000 0077ff}
${color  #0077ff}Proces:${color lightgrey} $processes  ${color  #0077ff}Run:${color lightgrey} $running_processes ${color  #0077ff}CPU:${color lightgrey} ${i2c temp 2}C${color lightgrey} ${color  #0077ff}MB:${color lightgrey} ${i2c temp 1}C

${color #0077ff}RAM:${color lightgrey} $mem/$memmax - $memperc% ${alignr}${color #0077ff}${membar 5,110}
${color #0077ff}SWP:${color lightgrey} $swap/$swapmax - $swapperc% ${alignr}${color #0077ff}${swapbar 5,110}

${color  #0077ff}HD IO: ${color lightgrey}${diskio} ${alignr}${color  #0077ff}Temperature: ${color lightgrey}${execi 10  /home/admin/.bin/hddconky}C
${color #0077ff}${diskiograph 000000 0077ff}

${color #0077ff}Hard Disks:
${color #0077ff} Root ${color lightgrey}${fs_used /}/${fs_size /}${alignr}${color #0077ff}${fs_bar 5,120 /}
${color #0077ff} Home ${color lightgrey}${fs_used /home}/${fs_size /home}${alignr}${color #0077ff}${fs_bar 5,120 /home}
${color  #0077ff} Data ${color lightgrey}${fs_used /media/data}/${fs_size  /media/data}${alignr}${color #0077ff}${fs_bar 5,120 /media/data}

${color #0077ff}CPU Usage         PID     CPU%   MEM%
${color lightgrey} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color #0077ff} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color #0077ff} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color #0077ff}Mem Usage
${color lightgrey} ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color #0077ff} ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color #0077ff} ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}

${color #0077ff}Network: ${color lightgrey}${addr eth0}

${color #0077ff}Down:${color lightgrey} ${downspeed eth0} k/s $alignr${color #0077ff} Up:${color lightgrey} ${upspeed eth0} k/s
${color  #0077ff}${downspeedgraph eth0 27,120 000000 0077ff 180} $alignr${color  #0077ff}${upspeedgraph eth0 27,120 000000 0077ff 25}
${color lightgrey}${totaldown eth0}           $alignr${color lightgrey}${totalup eth0}

${color #0077ff}Port(s)${alignr}#Connections
${color  #0077ff}Inbound: ${color lightgrey}${tcp_portmon 1 32767 count}   ${color #0077ff}Outbound: ${color lightgrey}${tcp_portmon 32768 61000  count}${alignr}${color #0077ff}Total: ${color lightgrey}${tcp_portmon 1  65535 count}

${color #0077ff}Inbound Connection ${alignr} Local Service/Port${color lightgrey}
 ${tcp_portmon 1 32767 rhost 0} ${alignr} ${tcp_portmon 1 32767 lservice 0}
 ${tcp_portmon 1 32767 rhost 1} ${alignr} ${tcp_portmon 1 32767 lservice 1}
 ${tcp_portmon 1 32767 rhost 2} ${alignr} ${tcp_portmon 1 32767 lservice 2}
 ${tcp_portmon 1 32767 rhost 3} ${alignr} ${tcp_portmon 1 32767 lservice 3}
 ${tcp_portmon 1 32767 rhost 4} ${alignr} ${tcp_portmon 1 32767 lservice 4}
 ${tcp_portmon 1 32767 rhost 5} ${alignr} ${tcp_portmon 1 32767 lservice 5}
 ${tcp_portmon 1 32767 rhost 6} ${alignr} ${tcp_portmon 1 32767 lservice 6}


```

---

### Post by deadflowr on 2014-02-23
What does the output say when you simply type
```
conky
```
in the terminal?
It should say invalid configuration file for the .conkyrc.
As well as other things.
and if not, what does
```
conky -c ~/.conkyrc
```
say?

Hint: press ctrl +c the cancel it, if needed.

---

### Post by pendulous on 2014-02-23
When I ran it as root, no error and it launches fine, but no custom config.

```
root@test:/tmp# conky
Conky: desktop window (180001c) is subwindow of root window (296)
Conky: window type - desktop
Conky: drawing to created window (0x4200001)
Conky: drawing to single buffer
```


as user:

```
test@test:~$ conky
Conky: /home/test/.conkyrc: 30: no such configuration: 'on_bottom'
Conky: /home/test/.conkyrc: 63: no such configuration: 'border_margin'
Conky: use_spacer should have an argument of left, right, or none.  'no' seems to be some form of 'false', so defaulting to none.
Conky: /home/test/.conkyrc: 94: no such configuration: 'xmms_player'
Conky: unknown variable freq_dyn
Conky: can't open '/sys/bus/i2c/devices/i2c-0/temp2_input': No such file or directory
please check your device or remove this var from Conky
Conky: Error destroying thread
Conky: Error destroying thread
Conky: Error destroying thread
Conky: Error destroying thread
Conky: Error destroying thread
***** Imlib2 Developer Warning ***** :
    This program is calling the Imlib call:

    imlib_context_free();

    With the parameter:

    context

    being NULL. Please fix your program.
```

This is an old config found on the forums, I don't use xmms_player. So what lines would I need to remove (or, apps to download, for temp2_input, etc) in order for it to work, with these items?


Removed lines in config: xmms player and changed no to none.

---

### Post by deadflowr on 2014-02-23
Well I decided to take this config and clean it up a little.
Here
```
background no
cpu_avg_samples 2
net_avg_samples 2
out_to_console no
use_xft yes
xftfont Bitstream Vera Sans Mono:size=8
own_window_transparent no
xftalpha 0.8
update_interval 1
own_window yes
own_window_transparent yes
own_window_hints undecorated,below,skip_taskbar
own_window_type override
double_buffer yes
minimum_size 260 5
maximum_width 260
draw_shades no
draw_outline no
draw_borders no
stippled_borders no
border_width 1
default_color white
default_shade_color white
default_outline_color white
gap_x 15
gap_y 70
alignment top_right
use_spacer right
no_buffers yes
uppercase no

TEXT
${color #0077ff}$sysname $kernel $machine - $nodename 

${color #0077ff}Uptime:${color lightgrey} $uptime ${color #0077ff} Load:${color lightgrey} $loadavg

${color  #0077ff}${execi 1000 cat /proc/cpuinfo | grep 'model name' | sed -n 1p | sed -e  's/model name.*: //'} ${color lightgrey}${freq 1}MHZ
${color #0077ff}Usage:${color #0077ff} ${color lightgrey}${cpu}% ${color #0077ff}${cpubar}
${color #0077ff}${cpugraph 000000 0077ff}
${color  #0077ff}Proces:${color lightgrey} $processes  ${color  #0077ff}Run:${color lightgrey} $running_processes #${color  #0077ff}CPU:${color lightgrey} ${i2c temp 2}C${color lightgrey} #${color #0077ff}MB:${color lightgrey} ${i2c temp 1}C

${color #0077ff}RAM:${color lightgrey} $mem/$memmax - $memperc% ${alignr}${color #0077ff}${membar 5,110}
${color #0077ff}SWP:${color lightgrey} $swap/$swapmax - $swapperc% ${alignr}${color #0077ff}${swapbar 5,110}

${color  #0077ff}HD IO: ${color lightgrey}${diskio} ${alignr}${color  #0077ff}
${color #0077ff}${diskiograph 000000 0077ff}

${color #0077ff}Hard Disks:
${color #0077ff} Root ${color lightgrey}${fs_used /}/${fs_size /}${alignr}${color #0077ff}${fs_bar 5,120 /}
${color #0077ff} Home ${color lightgrey}${fs_used /home}/${fs_size /home}${alignr}${color #0077ff}${fs_bar 5,120 /home}

${color #0077ff}CPU Usage         PID     CPU%   MEM%
${color lightgrey} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color #0077ff} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color #0077ff} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color #0077ff}Mem Usage
${color lightgrey} ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color #0077ff} ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color #0077ff} ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}

${color #0077ff}Network: ${color lightgrey}${addr eth0}

${color #0077ff}Down:${color lightgrey} ${downspeed eth0} k/s $alignr${color #0077ff} Up:${color lightgrey} ${upspeed eth0} k/s
${color  #0077ff}${downspeedgraph eth0 27,120 000000 0077ff 180} $alignr${color  #0077ff}${upspeedgraph eth0 27,120 000000 0077ff 25}
${color lightgrey}${totaldown eth0}           $alignr${color lightgrey}${totalup eth0}

${color #0077ff}Port(s)${alignr}#Connections
${color  #0077ff}Inbound: ${color lightgrey}${tcp_portmon 1 32767 count}   ${color #0077ff}Outbound: ${color lightgrey}${tcp_portmon 32768 61000  count}${alignr}${color #0077ff}Total: ${color lightgrey}${tcp_portmon 1  65535 count}

${color #0077ff}Inbound Connection ${alignr} Local Service/Port${color lightgrey}
 ${tcp_portmon 1 32767 rhost 0} ${alignr} ${tcp_portmon 1 32767 lservice 0}
 ${tcp_portmon 1 32767 rhost 1} ${alignr} ${tcp_portmon 1 32767 lservice 1}
 ${tcp_portmon 1 32767 rhost 2} ${alignr} ${tcp_portmon 1 32767 lservice 2}
 ${tcp_portmon 1 32767 rhost 3} ${alignr} ${tcp_portmon 1 32767 lservice 3}
 ${tcp_portmon 1 32767 rhost 4} ${alignr} ${tcp_portmon 1 32767 lservice 4}
 ${tcp_portmon 1 32767 rhost 5} ${alignr} ${tcp_portmon 1 32767 lservice 5}
 ${tcp_portmon 1 32767 rhost 6} ${alignr} ${tcp_portmon 1 32767 lservice 6}
```

I removed all the commented lines above TEXT.
removed on_bottom, changed user_space no to user_space right removed mail_spool $MAIL.
(I did something else, but forgot already, lol)

In The section after TEXT, I removed the Hard Disk entry for /media/data, because unless you make and mount that it probably doesn't exist.
I removed the section 
```
Temperature: ${color lightgrey}${execi 10  /home/admin/.bin/hddconky}C
${color #0077ff}${diskiograph 000000 0077ff}
```
Because chances are you, as I, don't have a file inside anything for /home/admin/.bin.
I also added comments to the CPU and MB temp settings
```
${color  #0077ff}CPU:${color lightgrey} ${i2c temp 2}C${color lightgrey} ${color  #0077ff}MB:${color lightgrey} ${i2c temp 1}C
```
to
```
**[COLOR=#0000ff]#[/COLOR]**${color  #0077ff}CPU:${color lightgrey} ${i2c temp 2}C${color lightgrey} ${color  #0077ff}MB:${color lightgrey} ${i2c temp 1}C
```

Well, see if any of these changes help.

Edit: I forgot I also added the line sed -n 1p to the line
```
${color  #0077ff}${execi 1000 cat /proc/cpuinfo | grep 'model name' | sed -n 1p | sed -e  's/model name.*: //'}
```
simply because it was posting two lines repeated.

---

### Post by pendulous on 2014-02-23
Hah, wow, thanks! Works like a charm; though, hadn't realized, forgot, how popular conky is since i've not used *nix in such a long time. Been busy searching google images on conky. 

Found one I'd like to use, but not sure where the source is: 
[IMG]http://imgbox.com/abpZqU2N[/IMG]
[http://imgbox.com/abpZqU2N](http://imgbox.com/abpZqU2N)

Needs some updating. Needs an analog berometer, etc for weather, and straight lines, no spheres or oblong images (other weather stuff) for data monitors images.

---

### Post by deadflowr on 2014-02-23
If you want some added fun check out the stuff sector11 and mrpeachy do.
[http://ubuntuforums.org/showthread.php?t=281865&page=2268](http://ubuntuforums.org/showthread.php?t=281865&page=2268)
Click their links.
Most of the stuff they do is posted on #! forums. FWIW.

---

