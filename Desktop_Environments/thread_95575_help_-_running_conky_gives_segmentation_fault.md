---
title: "help - running conky gives segmentation fault"
date: 2005-11-26
forum: Desktop Environments
---

### Post by 0okami on 2005-11-26
I installed Conky and when I type "conky" into a terminal, i get:

Conky: Xft not enabled.
Segmentation fault. 

and then it returns back to the terminal prompt. 
Any ideas whats going on?

---

### Post by taurus on 2005-11-26
How did you install conky, with synaptic (apt-get) or from source?  Also, look at your ~/.conkyrc and make sure you enable xft (as it says in the error message)...

use_xft yes

---

### Post by 0okami on 2005-11-26
[QUOTE=taurus]How did you install conky, with synaptic (apt-get) or from source?  Also, look at your ~/.conkyrc and make sure you enable xft (as it says in the error message)...

use_xft yes[/QUOTE]


I installed Conky through the terminal: 
sudo apt-get install conky

i will check into that ~/.conkyrc as soon as i get home :) 
thanks.

---

### Post by 0okami on 2005-11-26
[QUOTE=0okami]
i will check into that ~/.conkyrc as soon as i get home :) 
thanks.[/QUOTE]

Ok, i checked to see if that was in the conkyrc, and in fact it is set to yes. 

#use Xft
use_xft yes

Anything else I I should check for? Im still getting the same error.

---

### Post by taurus on 2005-11-27
Okay, what if you comment that line out by putting a "#" in front of it.  Then, start conkyrc again from a terminal...  Otherwise, either post your ~/.conkyrc or send it to me and I will have a look!

---

### Post by 0okami on 2005-11-27
[QUOTE=taurus]Okay, what if you comment that line out by putting a "#" in front of it.  Then, start conkyrc again from a terminal...  Otherwise, either post your ~/.conkyrc or send it to me and I will have a look![/QUOTE]


commenting out the line for Xft takes care of it reporting about xft... but segmentation fault is still there. 

this is my conkyrc file: 

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
#use_xft yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=8

own_window_transparent no
own_window_colour hotpink
# Text alpha when using Xft
xftalpha 0.8

on_bottom yes

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 1
# Create own window instead of using desktop (required in nautilus)
own_window no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer no

# Minimum size of text area
#minimum_size 280 5
#maximum_width 150

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 10

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
gap_x 13
gap_y 13
#alignment top_right
alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer no

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

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
#${font Luxi Mono:size=10}justo como este texto que o google traduz fÃªz o portuguÃªs
# stuff after 'TEXT' will be formatted on screen
#${font Grunge:size=12}${time %a  %b  %d}${alignr -25}${time %k:%M}

TEXT
$nodename - $sysname $kernel on $machine
$stippled_hr
${color lightgrey}Uptime:$color $uptime ${color lightgrey}- Load:$color $loadavg
${color lightgrey}CPU Usage:${color #5000a0} ${cpu}% ${cpubar}
${color black}${cpugraph 000000 5000a0}
${color lightgrey}RAM Usage:$color $mem/$memmax - $memperc% $membar
${color lightgrey}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar}
${color lightgrey}Processes:$color $processes  ${color grey}Running:$color $running_processes
$color$stippled_hr
${color lightgrey}Networking:
 Down:${color #8844ee} ${downspeed eth0} k/s${color lightgrey} ${offset 70}Up:${color #22ccff} ${upspeed eth0} k/s
${color black}${downspeedgraph eth0 32,150 ff0000 0000ff} $alignr${color black}${upspeedgraph eth0 32,150 0000ff ff0000}
${color lightgrey}File systems:
 / $color${fs_used /}/${fs_size /} ${fs_bar /}
${color lightgrey}Temperatures:
 CPU:$color ${i2c temp 2}C${color grey} - MB:$color ${i2c temp 1}C
${font Dungeon:style=Bold:pixelsize=12}${color #88aadd}MPD: ${alignc}$mpd_artist - $mpd_title
${color #88aadd}$mpd_bar
${color #88aadd}${alignc}$mpd_status
${color}Name              PID     CPU%   MEM%
${color #ddaa00} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color}Mem usage
${color #ddaa00} ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color lightgrey} ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color lightgrey} ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}



```

---

### Post by 0okami on 2005-11-27
what would be the most basic conkyrc config file one can create? i want to see if it will at least work with the most simple of config like... "Hello world" ?

---

### Post by taurus on 2005-11-27
Try to remove the "#" sign in front of "use_xft yes" since you are using xft font on the next line!!!

---

### Post by 0okami on 2005-11-27
[QUOTE=taurus]Try to remove the "#" sign in front of "use_xft yes" since you are using xft font on the next line!!![/QUOTE]

i tried that... it said Xft not enabled. Thats when i commented out "use_xft yes
" by suggestion... Xft error gone, segmentation fault still remains

Not sure what to do next except wait for someone to offer a sugestion. :)

---

### Post by ranf on 2005-11-28
[QUOTE=0okami]Xft error gone, segmentation fault still remains

Not sure what to do next except wait for someone to offer a sugestion. :)[/QUOTE]
If you didn't install `lm_sensors' or never even heard about it remove the line with `i2c'
```
${color lightgrey}Temperatures:
 CPU:$color ${i2c temp 2}C${color grey} - MB:$color ${i2c temp 1}C

```
And also the ones with `mpd'_something.

---

### Post by mcduck on 2005-11-28
I had the same problem with the Conky installed from repos. It segfaulted, whatever I had in conkyrc. I had to install .deb from Conky's web site to get it working, you could give it a try.

---

### Post by ppmt on 2005-11-28
Hi,

[QUOTE=ranf]If you didn't install `lm_sensors' or never even heard about it remove the line with `i2c'
```
${color lightgrey}Temperatures:
 CPU:$color ${i2c temp 2}C${color grey} - MB:$color ${i2c temp 1}C

```
And also the ones with `mpd'_something.[/QUOTE]

Spot on. I had the same problem. I installed conky then I installed lm_sensors because I saw conky could measure the cpu temperature.

I couldn't get lm-sensors to work but conky was ok. Then I rebooted the PC and after that conky wouldn't work :(

Removing the 2 line related to lm_sensors fix conky. 

Strangely enough lm-sensors now work but obviously conky is not happy with it...

Edit: I actually fixed my lm_sensors issue now. The answer is on the conky forum.

[http://sourceforge.net/forum/forum.php?thread_id=1365287&forum_id=481811]("http://sourceforge.net/forum/forum.php?thread_id=1365287&forum_id=481811")

---

### Post by 0okami on 2005-11-29
[QUOTE=mcduck]I had the same problem with the Conky installed from repos. It segfaulted, whatever I had in conkyrc. I had to install .deb from Conky's web site to get it working, you could give it a try.[/QUOTE]

looking at the website [http://conky.sourceforge.net](http://conky.sourceforge.net) , i follow the links to download conky 1.3.4 .. however, im not seeing a *.deb in that package:  
conky-1.3.4.tar.bz2 platform imdependant. I do see one but that is for AMD64. my cpu is just a normal AMD athlon XP 2500... 

Do i have to compile this ? (i have never done that before) ...
edit: n/m. i found an older version on sourceforge that i will try..

---

### Post by 0okami on 2005-11-29
ok, installing the version conky_1.3.0-1_i386.deb found on sourceforge and followign the instructions along with the two lines that I was told to remove...

 Conky is now up and running for me. Cant wait to get home and see it in person. (currently setting it via vnc client on dialup... ew. )

---

### Post by Luggy on 2005-11-29
I would recommend downloading the sources,
[http://prdownloads.sourceforge.net/conky/conky-1.3.4.tar.bz2?download](http://prdownloads.sourceforge.net/conky/conky-1.3.4.tar.bz2?download)
and compiling them,
> Compiling from source

You'll need the X11 development libraries, version 6.8.2 or later. package name is probably libx11-dev

   1. ./configure
   2. make
   3. make install (optional. if you don't do this, the conky executable will be in src/ )

[http://conky.sourceforge.net/](http://conky.sourceforge.net/)
I recommend sudo make install.

If you are having trouble with the sensors I would recommend taking out that in the ~/.conkyrc. I was having problems getting them to work due to my default Hoary kernel not having support for them. I don't know if default Breezy supports them, if not just take out the line or edit your kernel.

If you are using Gnome check out link [http://conky.sourceforge.net/gnome.html](http://conky.sourceforge.net/gnome.html).
They talk about making conky run as it's own window *("conky -o" I believe)* and they come up with this complex solution to solve the problem with it only existing on one virtual desktop. 

The easiest thing to do is to simply right click on conky window at your bottom task bar and select "Always Visible on Workspace".

Maybe I should go and write my own Howto Conky one of these days.

---

### Post by mcduck on 2005-11-29
Well, Devilspie is a nice solution to getting conky live nicely with gnome..

If you have trouble with your sensors, but lm-sensors works fine, you should just point conky to the right device.

By the way, I have a bit of annoying problem with the top-display in Conky. It works ok most of the time, but some programs give insane readings. I just ripped a CD with Grip, and conky says lame used 169% CPU, Grip 23% etc.. On the other side, overall CPU use is only slightly over 40% ;)

---

### Post by jtan325 on 2005-11-29
[QUOTE=0okami]ok, installing the version conky_1.3.0-1_i386.deb found on sourceforge and followign the instructions along with the two lines that I was told to remove...

 Conky is now up and running for me. Cant wait to get home and see it in person. (currently setting it via vnc client on dialup... ew. )[/QUOTE]

There is a 1.3.3-1_i386.deb in case you missed that. I did the .deb packaging, and am going to produce a 1.3.4 soon. hopefully I can get the MOTUs to replace the crappy non-xft one in the repos with 1.3.4 soon...

---

### Post by mcduck on 2005-11-29
That would be nice, as release notes for 1.3.4 say that some issues with top code have been fixed. That might solve my problems with funny CPU usage percents.

---

### Post by skullosorus on 2007-03-01
Thank you, this post helped determine my problem also :)

---

