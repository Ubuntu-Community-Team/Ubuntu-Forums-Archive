---
title: "Conky flickering in Gutsy"
date: 2007-11-03
forum: Desktop Effects &amp; Customization
---

### Post by panther_sn on 2007-11-03
Hi all I am running Gutsy, and conky 1.4.7,  I am having a problem where Conky keeps flickering.
I am running conky with the following conkyrc

```
#Conkyrc by Panther_sn
#http://ubuntu-os.freehostia.com

# Create own window instead of using desktop (required in nautilus)
own_window_transparent yes
own_window yes
own_window_type desktop
own_window_hints below

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 200 300
maximum_width 300

# Draw shades?
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors
default_color white
default_shade_color black
default_outline_color white

own_window_colour black
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 30
gap_y 30

# stuff after 'TEXT' will be formatted on screen
override_utf8_locale no
xftfont Terminus:size=10
xftalpha 0.8


TEXT

$color$nodename:
$sysname $kernel on $machine
Uptime: $uptime  @  ${time %I:%M:%S}
${time %A} ${time %e %B %G} 


System:

cpu: ${freq} MHz  $cpu%
load: ${cpu}%
ram: $mem/$memmax , $memperc%
avg load: $loadavg
processes: $processes	running: $running_processes


File Systems:

MEM:  $memperc% $mem/$memmax

SWAP: $swapperc% $swap/$swapmax


ROOT:    ${color }${fs_used /}/${fs_size /}

HOME:    ${color }${fs_used /home}/${fs_size /home}


Networking:

IP address: $color${execi 43200 curl 'http://www.whatismyip.org' | fold -w50}

down: $color${downspeed eth0}k/s  Total Downloaded: ${totaldown eth0}
${downspeedgraph eth0 25,140 ffffff ff0000} 
up: $color${upspeed eth0}k/s  Total Uploaded: ${totalup eth0}
${upspeedgraph eth0 25,140 ffffff ff0000}


Fortune:
${execi 1200 fortune -s | fold -w50}
```



And this is the Modules section from my xorg.conf
```
Section "Module"
	Load "glx"
	Load "dbe"
EndSection
```

I was wondering if any1 has any ideas on how to stop the horrid flickering .

Thanks

---

### Post by juyanith on 2007-11-03
I found an answer here: [https://bugs.launchpad.net/ubuntu/+source/conky/+bug/42467](https://bugs.launchpad.net/ubuntu/+source/conky/+bug/42467)

Basically, add Load "dbe" to your xorg.conf and it should allow conky to use double buffering.

---

### Post by panther_sn on 2007-11-03
Thanks for  your help but as you can see I already have Load "dbe" in my xorg.conf, and unfortunately it isa not helping, any other ideas?

---

### Post by panther_sn on 2007-11-04
bump, I really hope some1 has some other ideas, that I might not have tried

---

### Post by juyanith on 2007-11-04
I should have been more clear, adding the "dbe" module seems to have worked for me with 7.04, but apparently doesn't work for you in 7.10. Does conky give you any error message? If it says something like about being unable to use double buffering maybe there is some other module that it needs. 

My module section in xorg.conf looks like this:
```

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "type1"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
    Load           "dbe"
EndSection

```

I did try the .conkyrc file you posted and didn't see any flicker, so I don't believe it is a setting there. Sorry, but that's the best help I can offer.

---

### Post by isecore on 2007-11-10
I also have problems with conky flickering. It worked flawlessly under Feisty, but since upgrading to Gutsy it flickers. My xorg.conf has the dbe-module loaded and conky confirms that it's using double buffering when starting it - yet it flickers when it refreshes.

Would be nice if anyone knew anything about it.

---

### Post by aparigraha on 2007-11-22
I have the same issue with flickering although "dbe" is used in xorg.conf, conky still fails to use double buffer when started. Any ideas?

---

### Post by Ub1476 on 2007-11-27
> **aparigraha said:**
> I have the same issue with flickering although "dbe" is used in xorg.conf, conky still fails to use double buffer when started. Any ideas?

Yes!

I just noticed that Conky only flickers when there is a conky code/variable which is wrong, mean something it cannot understand. 

Say, I were tuning Conky a little to show what Music I were playing (Exaile), and added this:

```
${execi 10 exaile --get-title} - ${execi 10 exaile --get-artist} - ${execi 10 exaile --get-status}
```

The wrong part here is "${execi 10 exaile --get-**status**}". I hoped that this would show how much played and how much left of the song, but since that variable (status) doesn't exist, Conky started to flicker in confusion. 

When I removed that, Conky works perfect.:)

If you are not sure what variable is wrong, run conky in the terminal and it will start giving error messages about a wrong variable (for every message it flickers). 

Hope that fixes it for everybody!

By the way, If someone know a few good variables for Exaile that would be great.

---

### Post by isecore on 2007-11-27
> **Ub1476 said:**
> Yes!

I just noticed that Conky only flickers when there is a conky code/variable which is wrong, mean something it cannot understand. 

Say, I were tuning Conky a little to show what Music I were playing (Exaile), and added this:

```
${execi 10 exaile --get-title} - ${execi 10 exaile --get-artist} - ${execi 10 exaile --get-status}
```

The wrong part here is "${execi 10 exaile --get-**status**}". I hoped that this would show how much played and how much left of the song, but since that variable (status) doesn't exist, Conky started to flicker in confusion. 

When I removed that, Conky works perfect.:)

If you are not sure what variable is wrong, run conky in the terminal and it will start giving error messages about a wrong variable (for every message it flickers). 

Hope that fixes it for everybody!

By the way, If someone know a few good variables for Exaile that would be great.

Sorry, my man, but this isn't the solution. I was hoping it was this simple, but after examining the terminal output of my conky it still flickers occasionally without reporting any bad variables.

Either that or I'm doing something wrong :) but it seems like it's more complicated than this.

---

### Post by Ub1476 on 2007-11-27
Remember to add "dbe" to your  module list.

You might want to try my conkyrc though, for a quick examination:)

 ```
# mod by uel
avoid flicker
double_buffer yes
no_buffers yes
 
#own window to run simultanious 2 or more conkys
own_window yes
own_window_transparent yes
own_window_type normal
own_window_hints undecorate,sticky,skip_taskbar,skip_pager
  
#borders
#draw_borders no
#border_margin 1
  
#shades
draw_shades no
#draw_graph_borders yes
#draw_borders yes
  
position
gap_x 1
gap_y 788
alignment bottom_left
  
behaviour
update_interval 1
  
#colour
default_color 000000
#default_color D6D6D6
#default_color bfbfbf
#default_shade_color 000000
own_window_colour 202020
#draw_borders_colour 000000
#draw_graph_borders_colour 000000
#484432 95956B
  
#font
use_xft yes
xftfont HandelGotD:pixelsize=10
  
#to prevent window from moving
use_spacer no
minimum_size 1278 10
 
#mpd
mpd_host localhost
mpd_port 6600
# ${offset -22}
TEXT
${voffset -1} Cpu: ${color 225E00}${font}${cpu}% ${color 292929}${color} P: ${color 225E00}${font}${processes}${color} R: ${color 225E00}${font}${running_processes}${color 292929} |${color} Mem: ${color 225E00}${font}${mem}${color} Swap: ${color 225E00}${font} ${swap} ${color 292929} | ${color} Uptime: ${color 225E00}${font}${uptime_short}${color 292929} | ${color 225E00}${font}${downspeed eth1} Kb/s ${color} ${totaldown eth1} down${color 292929}  | ${color} ${color 225E00}${upspeed eth1} Kb/s ${color} ${totalup eth1} up${color 292929}  |  ${color}Size: ${color 225E00}${font}${fs_size /} ${color} Left: ${color 225E00}${font}${fs_free /home/kasper} ${color 292929}|  ${color} Battery:${color 225E00} ${battery}${color} |  Temp: ${color 225E00}${font}${acpitemp}${color}C ${color 292929} | ${color 225E00}${color} Music: ${color 225E00}${font}${execi 10 exaile --get-title}${color 225E00}${alignr}${color}${time %A, %d %B} ${color}${time  %H:%M}


```

---

### Post by Ub1476 on 2007-11-28
I also noticed now that Conky start flickering when some text override each other. This could happen if you have set default positions (x,y) for a variable and another variable has more to display than you expected (say a music variable which suddenly shows a long title/artist name).

Picture examples:

---

### Post by panther_sn on 2007-12-01
Ok what I have found is that Conky although using double buffering 
```
taz@taz-desktop:~$ conky
Conky: desktop window (a000c0) is subwindow of root window (52)
Conky: window type - desktop
Conky: drawing to created window (3800001)
Conky: drawing to double buffer

```
Seems to be flickering for me only when executing
```

${execi 1200 fortune | fold -w45 -s}

```
Which I am assuming is to do with the execi command, has any1 got suggestions to fix that problem?

---

### Post by lvleph on 2008-01-06
I seem to have the same issue with execi commands. I use 5 or more of them in my .conkyrc any help is greatly appreciated.

```
# UBUNTU-CONKY.
#

# Update interval in seconds
update_interval 1.0
total_run_times=0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
#minimum_size 250 5
maximum_width 250

draw_shades no
draw_outline no # amplifies text if yes
draw_borders no
draw_graph_borders no

use_xft yes
xftalpha 0.9
xftfont Candera:size=8
uppercase no
override_utf8_locale yes
use_spacer no

stippled_borders 3
border_margin 9
border_width 10

# Gap between borders of screen and text
gap_x 10
gap_y 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey
color0 97b9f4
color1 orange
color2 red
color3 green

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right


# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${color0}${font Arial:bold:size=12}${time %H:%M:%S}$font
${time %A}, ${time %d %B %G}$color
${color1}$hr
${voffset -3}$alignc GMAIL
${voffset -9}$hr $color
${voffset -5}${color}You have ${color3}${texeci 100 python ~/scripts/gmail.py} ${color}new email(s).
${if_empty ${execi 100 python ~/scripts/gmail_subj.py}}${color1}$hr
${voffset -3}$alignc 4 DAY FORECAST
${voffset -9}$hr $color
${else}${execi 100 python ~/scripts/gmail_subj.py}
${color1}$hr
${voffset -3}$alignc 4 DAY FORECAST
${voffset -9}$hr $color${endif}
${voffset -10}${font weather:size=50}${alignc}${execi 60000 ~/scripts/weather.sh USVA0652 f p}${execi 60000 ~/scripts/weather.sh USVA0652 f 2p}${execi 60000 ~/scripts/weather.sh USVA0652 f 3p}${execi 60000 ~/scripts/weather.sh USVA0652 f 4p}${font}$color
${alignc}${offset -10}${execi 60000 ~/scripts/weather.sh USVA0652 f t}${offset 8}${execi 60000 ~/scripts/weather.sh USVA0652 f 2}${offset 8}${execi 60000 ~/scripts/weather.sh USVA0652 f 3}${offset 8}${execi 60000 ~/scripts/weather.sh USVA0652 f 4}
${color1}$hr
${voffset -3}$alignc SYSTEM
${voffset -9}$hr $color
${exec cat /etc/issue.net}
$sysname Kernel $kernel ($machine)
Uptime: $uptime
Battery status: $acpiacadapter, $battery 
${color1}$hr
${voffset -3}$alignc PROCESSES
${voffset -9}$hr $color
${alignc}Processes: $processes  Running: $running_processes
${color1}NAME $alignr PID      CPU%     MEM%$color
${top name 1}${alignr}${top pid 1}    ${top cpu 1}     ${top mem 1}
${top name 2}${alignr}${top pid 2}    ${top cpu 2}     ${top mem 2}
${top name 3}${alignr}${top pid 3}    ${top cpu 3}     ${top mem 3}
${color1}$hr
${voffset -3}$alignc CPU/MEM
${voffset -9}$hr $color
${voffset -5}${cpugraph 50,250 000000 ff0000}
${voffset -55}${execi 1000 head /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //' | cut -b 0-20,31-48}
Clock: ${freq}MHz${alignr}Usage: ${cpu}%        Temp: ${acpitemp}C
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color
${color1}$hr
${voffset -3}$alignc FILE SYSTEM
${voffset -9}$hr $color
Root:  ${fs_free}/${fs_size /} ${fs_bar 6 /}
Home:  ${fs_free /home}/${fs_size /home} ${fs_bar 6 /home}
${if_mounted /media/samba/}Samba:  ${fs_free /media/samba}/${fs_size /media/samba} ${fs_bar 6 /media/samba}
${color1}$hr 
${else}${color1}$hr $endif
${voffset -3}$alignc NETWORK
${voffset -9}$hr $color
${if_empty ${exec python ~/scripts/wifiUp.py}}${voffset -5}${downspeedgraph eth0 55,124 000000 ff0000} ${upspeedgraph eth0 55,124 000000 00ff00}$color
${voffset -60}${alignc}WIRED
Local IP: ${addr eth0} $alignr Public IP: ${execi 18000 ~/scripts/myip.sh}
Down: ${downspeed eth0} kb/s $alignr Up: ${upspeed eth0} kb/s
Total: ${totaldown eth0} $alignr Total: ${totalup eth0}
${else}${voffset -5}${downspeedgraph wlan0 64,124 000000 ff0000} ${upspeedgraph wlan0 64,124 000000 00ff00}$color
${voffset -69}${alignc}ESSID:"${wireless_essid wlan0}"
Local IP: ${addr wlan0} $alignr Public IP: ${execi 1800 ~/scripts/myip.sh}
Signal: ${execi 1800 ~/scripts/wifiQ.sh}% $alignr Bit Rate: ${execi 18000 ~/scripts/wifiBR.sh} Mb/s
Down: ${downspeed wlan0} kb/s $alignr Up: ${upspeed wlan0} kb/s
Total: ${totaldown wlan0} $alignr Total: ${totalup wlan0}$endif
```

---

### Post by oxxxid on 2008-01-10
Try changing your conky config file to something like this. It worked for me

```
#own window to run simultanious 2 or more conkys
own_window yes
own_window_transparent yes
own_window_type override

```

---

### Post by lvleph on 2008-01-10
I already have that.

---

### Post by sunv on 2008-03-12
Mine used to flicker but I figured out why it was doing it, and now its not doing it anymore
When my conky used to flicker, one of the lines of text on my conky was really long.  So long that it seemed to stick out of the minimum space I set for conky to use.  that caused it to flicker.  It was the cpufreq line and it would usually start with 3 digits when i loaded up conky, (768Mhz for instance), but sometimes would jump to 4 digits and it would start to flicker (1768).  So I realized anytime something went out of the set conky space, it would flicker.

I shortened the line, and it doesn't flicker anymore.  It only flickers when im using mpd and the song name is really long and it gets pushed outside of the conky box.  But im sure I could just make the space bigger.

There should be a command that sets ur minimum conky space or seomthing like that.  Change it, or change the text so that it isn't extremely long and sticking out of the box,  and see if it still flickers.

---

### Post by lvleph on 2008-03-13
I use text wrapping in the scripts I wrote, and everything I use in my conky is a script I wrote. However, mine still flickers. From my experience it only flickers when the number of lines change, i.e. the size of the conky window changes.

---

### Post by mlapaglia on 2008-04-04
i set the minimum size for my window to a larger amount than my longest line of text could go and that seems to have stopped the flickering for me :)

---

### Post by Spike-X on 2008-04-25
Setting own_window to no fixed it for me.

---

### Post by BLTicklemonster on 2008-07-04
I've tried all of these, and still get flickering. Hardy.

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
# around
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
own_window no
own_window_type desktop

# If own_window is yes, you may use type normal, desktop or overide
own_window_type normal

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window_transparent is set to no, you can set the background colour here
#own_window_colour

# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 360 5

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline yes

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 8 no

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color light blue
default_shade_color black
default_outline_color black

# Text alignment, other possible values are commented
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right
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
use_spacer none

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
HomeBrew Box

${color}Uptime:$color $uptime ${color}- Load:$color $loadavg

${color}AMD 64bit ${execi 1000 cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.* //'} ${color}Running at:${freq_dyn}Mhz
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
 disk-1 $color${fs_used /media/disk-1}/${fs_size /media/disk-1} ${fs_bar /media/disk-1}
 STORAGE $color${fs_used /media/STORAGE}/${fs_size /media/STORAGE} ${fs_bar /media/STORAGE}
 disk $color${fs_used /media/disk}/${fs_size /media/disk} ${fs_bar /media/disk}
 XP $color${fs_used /media/disk-2}/${fs_size /media/disk-2} ${fs_bar /media/disk-2}
 Hardy2 $color${fs_used /media/disk-4}/${fs_size /media/disk-4} ${fs_bar /media/disk-4}
 MOVIES $color${fs_used /media/MOVIES}/${fs_size /media/MOVIES} ${fs_bar /media/MOVIES}
${color}Name              PID     CPU%   MEM%
${color} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}
${color}Mem usage
${color} ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color} ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color} ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}
```


*EDIT:

heh heh my bad.

add this:

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

it even says flicker right there in the open.

Took care of it for me.

Edited the code above to show what I am running now.

---

