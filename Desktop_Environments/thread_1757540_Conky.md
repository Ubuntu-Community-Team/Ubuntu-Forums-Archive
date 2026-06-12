---
title: "Conky"
date: 2011-05-13
forum: Desktop Environments
---

### Post by Frogs Hair on 2011-05-13
I have been interested in installing Conky a while , so I went looking for instructions for a ready made configuration.

I installed lm-sensors and the conky-all package and went looking for a horizontal theme for the bottom of the screen , which I found .

The instructions I used stated that I needed create a .conkyrc folder in hidden folders and place my .conkeyrc file inside . The only way I could do this was to create a folder of a different name , move the rc file into the folder and rename the folder because the file name was already in use. 

After about an hour of no joy I deleted the folder and downloaded a new .conkyrc and placed it directly in home/hidden with no folder and I was up and running.

The script I have is supposed to be able to work with nautilus , but when clicked on the screen Conky disappeared. so with the help of Google changed a line in the .conkyrc 

```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
#own_window_hints yes

``` I changed own_window_type from desktop to override

Can some one point me to a good tutorial so others don't have go though the same thing.

---

### Post by stinkeye on 2011-05-13
[**_[COLOR="DarkRed"]HOW TO: A Beginners Guide to Setting up Conky[/COLOR]_**]("http://ubuntuforums.org/showthread.php?p=5436679#post5437628")

When you use 
```
own_window_type override
```
own_window_hints have no meaning and are ignored and no shadow is drawn around conky.


If you use
```
own_window_type normal
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```
a shadow will be drawn around conky.

When you run conky it will look for a config file @ **~/.conkyrc**
If there is no ~/.conkyrc file it will run the default config @ **/etc/conky/conky.conf**


Alternatively you can run any saved conky config with
conky -c [COLOR="DimGray"]/path/to/your/config[/COLOR]


eg I have a ~/conky/conkydemo file that I paste in conkys from the forums to test and just run
```
conky -c ~/conky/conkydemo
```

---

### Post by Frogs Hair on 2011-05-13
Thank You !!

I will put this to good use , after some failed attempts with start up scrips this may will help because none of those have worked either.

---

### Post by Frogs Hair on 2011-05-13
When I try this , my GTK theme places a title bar on top of Conky .
```
own_window_type normal
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```

---

### Post by stinkeye on 2011-05-13
> **Frogs Hair said:**
> When I try this , my GTK theme places a title bar on top of Conky .
```
own_window_type normal
own_window_hints **undecorated**,below,sticky,skip_taskbar,skip_pager
```
It shouldn't do if you have both of those settings.
Check that you don't have similar conflicting settings.

**own_window_type override** is what a lot of configs use.

I just prefer **own_window_type normal** because it allows you to move the window with alt+mouse1.

---

### Post by Frogs Hair on 2011-05-13
I copied and pasted as you wrote it . This is fine as is because the theme is laid out well and looks better to me without the shadow . I was going to provide a link to the theme , but Gnome Look is down at the moment. I tried another method a day ago and it also added a title bar. I will try a different theme and see what happens. Changing the GTK theme makes no difference .

---

### Post by ManualSparrow on 2011-05-13
Are you using compiz? If the window hints aren't working for you, you can go into the window decorator settings and set exceptions so that specified windows don't get decorated or have shadows.

Also, why was the .conky folder name already taken? It is pretty handy to just put all your conky files in that folder then launch them with a script.

---

### Post by stinkeye on 2011-05-13
> **Frogs Hair said:**
> I copied and pasted as you wrote it . This is fine as is because the theme is laid out well and looks better to me without the shadow . I was going to provide a link to the theme , but Gnome Look is down at the moment. I tried another method a day ago and it also added a title bar. I will try a different theme and see what happens. Changing the GTK theme makes no difference .
Post your conky config so I can test it.

---

### Post by Frogs Hair on 2011-05-13
> **ManualSparrow said:**
> Are you using compiz? If the window hints aren't working for you, you can go into the window decorator settings and set exceptions so that specified windows don't get decorated or have shadows.

Also, why was the .conky folder name already taken? It is pretty handy to just put all your conky files in that folder then launch them with a script.

I named the theme file .conkyrc and saved it on Gedit per the instructions I found on line , so when I created the .conkyrc folder I was asked if I wanted to replace the file for the folder. I am using Unity with compiz and the cube is enabled. Conky would not run from the folder.

---

### Post by Frogs Hair on 2011-05-13
> **stinkeye said:**
> Post your conky config so I can test it.

I have it set to override and this is on Unity with compiz .
```
# conky configuration
# edited by darcon@gmail.com

# set to yes if you want Conky to be forked in the background
background yes

disable_auto_reload no
maximum_width 1200

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
#xftfont Bitstream Vera Sans Mono:size=8
xftfont Terminus:size=8

# Text alpha when using Xft
xftalpha 0.8

# Print everything to console?
# out_to_console no

# mail spool
#mail_spool $MAIL

# Update interval in seconds
update_interval 2.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
#own_window_hints yes


# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 10 5

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
#stippled_borders 8

# border margins
border_inner_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color white

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_middle

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 5
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
override_utf8_locale yes


# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer right


# stuff after 'TEXT' will be formatted on screen

TEXT
${color slate grey}Highest CPU:       ${goto 180}${color slate grey}Highest MEM: ${goto 350}${color slate grey}MEM: $color  ${membar 3,100} $memperc% ${goto 530}($mem ${goto 590}/ $memmax) ${goto 700}${color slate grey}Date:    $color ${time %a, %e %B %G  %H:%M:%S}
${color #ddaa00} ${top name 1}${top_mem cpu 1}     ${goto 180}${color #ddaa00} ${top_mem name 1}${top_mem mem 1} ${goto 350}${color slate grey}SWAP: $color ${swapbar 3,100} $swapperc% ${goto 530}($swap${goto 590}/ $swapmax) ${goto 700}${color slate grey}UpTime: $color  $uptime
${color lightgrey} ${top name 2}${top cpu 2}      ${goto 180}${color lightgrey} ${top_mem name 2}${top_mem mem 2} ${goto 350}${color slate grey}ROOT: ${color} ${fs_bar 3,100 /} ${fs_used_perc /}% ${goto 530}(${fs_free /} ${goto 590}/ ${fs_size /}) ${goto 700}${color slate grey}Kernel:${color}   $kernel
${color lightgrey} ${top name 3}${top cpu 3}      ${goto 180}${color lightgrey} ${top_mem name 3}${top_mem mem 3} ${goto 350}${color slate grey}HOME: ${color} ${fs_bar 3,100 /home} ${fs_used_perc /home}% ${goto 530}(${fs_free /home} ${goto 590}/ ${fs_size /home}) ${goto 700}${color slate grey}CPU Temp:${color} ${hwmon temp 1}Â°C
$hr
${color slate grey}NET:$color ${goto 100}${upspeedgraph eth0 20,130 000000 ffffff} ${goto 350}${downspeedgraph eth0 20,130 000000 ffffff} ${goto 500}${color slate grey}CPU:${color} $cpu% ${goto 560}${cpugraph 20,130 000000 ffffff}
${voffset -20}${color}Up: ${upspeed eth0} k/s ${goto 235} ${color}Down: ${color }${downspeed eth0}k/s ${goto 500}$color(${freq_g cpu0}Ghz) ${goto 720}${color slate grey}Load: ${color }$loadavg

```

---

### Post by stinkeye on 2011-05-13
Try this one.
I added some ${goto xx} commands to make it line up better and stop
flickering due to conky resizing.
```
# conky configuration
# edited by darcon@gmail.com

# set to yes if you want Conky to be forked in the background
background yes

disable_auto_reload no
maximum_width 920
minimum_size 920
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
#xftfont Bitstream Vera Sans Mono:size=8
xftfont Terminus:size=8

# Text alpha when using Xft
xftalpha 0.8

# Print everything to console?
# out_to_console no

# mail spool
#mail_spool $MAIL

# Update interval in seconds
update_interval 2.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
#own_window_hints undecorated,below,skip_taskbar,skip_pager


# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
#minimum_size 10 5

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
#stippled_borders 8

# border margins
border_inner_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color white

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_middle

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 5
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
override_utf8_locale yes


# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer right
short_units yes
pad_percents 0

# stuff after 'TEXT' will be formatted on screen

TEXT
${color slate grey}Highest CPU:       ${goto 180}${color slate grey}Highest MEM: ${goto 350}${color slate grey}MEM:$color${goto 390}${membar 3,100} $memperc% ${goto 530}($mem ${goto 590}/ $memmax) ${goto 700}${color slate grey}Date:${alignr 5}$color${time %a, %e %B %G  %H:%M:%S}
${color ddaa00} ${top name 1}${goto 100}${top_mem cpu 1}     ${goto 180}${color ddaa00} ${top_mem name 1}${goto 280}${top_mem mem 1} ${goto 350}${color slate grey}SWAP:$color${goto 390}${swapbar 3,100} $swapperc% ${goto 530}($swap${goto 590}/ $swapmax) ${goto 700}${color slate grey}UpTime:${alignr 5}$color$uptime
${color lightgrey} ${top name 2}${goto 100}${top cpu 2}      ${goto 180}${color lightgrey} ${top_mem name 2}${goto 280}${top_mem mem 2} ${goto 350}${color slate grey}ROOT:${color}${goto 390}${fs_bar 3,100 /} ${fs_used_perc /}% ${goto 530}(${fs_free /} ${goto 590}/ ${fs_size /}) ${goto 700}${color slate grey}Kernel:${color}${alignr 5}$kernel
${color lightgrey} ${top name 3}${goto 100}${top cpu 3}      ${goto 180}${color lightgrey} ${top_mem name 3}${goto 280}${top_mem mem 3} ${goto 350}${color slate grey}HOME:${color}${goto 390}${fs_bar 3,100 /home} ${fs_used_perc /home}% ${goto 530}(${fs_free /home} ${goto 590}/ ${fs_size /home}) ${goto 700}${color slate grey}CPU Temp:${color}${alignr 5}${hwmon temp 1}°C
$hr
${color slate grey}NET:$color ${goto 100}${upspeedgraph eth0 20,130 000000 ffffff} ${goto 350}${downspeedgraph eth0 20,130 000000 ffffff} ${goto 500}${color slate grey}CPU:${color} $cpu% ${goto 560}${cpugraph 20,130 000000 ffffff}
${voffset -20}${color}Up: ${upspeed eth0}${goto 235} ${color}Down: ${color}${downspeed eth0}${goto 500}$color(${freq_g cpu0}Ghz) ${goto 720}${color slate grey}Load: ${color }$loadavg
```


You can run as **own_window_type normal**
by changing override to normal
and uncommenting the line **#own_window_hints undecorated,below,skip_taskbar,skip_pager**

---

### Post by ManualSparrow on 2011-05-14
Re: Autostart
You can autostart via script by creating a blank file and renaming it conky_start in your home directory. Right-click>Permissions>Allow Executing File as a Program>Check yes.

Open the file, paste this inside:

```
#!/bin/bash
 sleep 10 && 
conky -c ~/.conkyrc;
```

Go to System>Startup Applications and click the + or Add button. Browse to the conky_start file (which should be in the home folder, path ~/conky_start) and click ok. Now this script should run on startup and after ten seconds start conky. This lets other things load first, such as compiz.
If that doesn't work and you are only using a single config file .conkyrc in the home folder, try using ```
#!/bin/bash
 sleep 10 && conky;
``` in conky_start instead. If you do want to use more than one conky (ie, start more than one conky window) you can add start them all at the same time ```
#!/bin/bash
 sleep 10 && 
conky -c ~/.conky1;
conky -c ~/.conky2;
conky -c ~/.conky3

```
etc. Just note that 
a) you need to get the path to the files right (in this case they would all be in the home folder and hidden, as per the added '.') 
b) it doesn't matter what you call the files if you use the longer versions - putting ```
conky -c PATH/TO/FILENAME
``` will start it up.

Re: compiz
If your windows are still looking goofy you can go to System Preferences>Compiz Config>Window Decorator>Rules>Add Rule>click on the running conky window>change selection to 'invert'>shadows, skip, etc. 
In this way Compiz inverts the rule and DOESN'T decorate conky.

---

### Post by Frogs Hair on 2011-05-14
> **stinkeye said:**
> Try this one.
I added some ${goto xx} commands to make it line up better and stop
flickering due to conky resizing.
```
# conky configuration
# edited by darcon@gmail.com

# set to yes if you want Conky to be forked in the background
background yes

disable_auto_reload no
maximum_width 920
minimum_size 920
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
#xftfont Bitstream Vera Sans Mono:size=8
xftfont Terminus:size=8

# Text alpha when using Xft
xftalpha 0.8

# Print everything to console?
# out_to_console no

# mail spool
#mail_spool $MAIL

# Update interval in seconds
update_interval 2.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
#own_window_hints undecorated,below,skip_taskbar,skip_pager


# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
#minimum_size 10 5

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
#stippled_borders 8

# border margins
border_inner_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color white

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_middle

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 5
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
override_utf8_locale yes


# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer right
short_units yes
pad_percents 0

# stuff after 'TEXT' will be formatted on screen

TEXT
${color slate grey}Highest CPU:       ${goto 180}${color slate grey}Highest MEM: ${goto 350}${color slate grey}MEM:$color${goto 390}${membar 3,100} $memperc% ${goto 530}($mem ${goto 590}/ $memmax) ${goto 700}${color slate grey}Date:${alignr 5}$color${time %a, %e %B %G  %H:%M:%S}
${color ddaa00} ${top name 1}${goto 100}${top_mem cpu 1}     ${goto 180}${color ddaa00} ${top_mem name 1}${goto 280}${top_mem mem 1} ${goto 350}${color slate grey}SWAP:$color${goto 390}${swapbar 3,100} $swapperc% ${goto 530}($swap${goto 590}/ $swapmax) ${goto 700}${color slate grey}UpTime:${alignr 5}$color$uptime
${color lightgrey} ${top name 2}${goto 100}${top cpu 2}      ${goto 180}${color lightgrey} ${top_mem name 2}${goto 280}${top_mem mem 2} ${goto 350}${color slate grey}ROOT:${color}${goto 390}${fs_bar 3,100 /} ${fs_used_perc /}% ${goto 530}(${fs_free /} ${goto 590}/ ${fs_size /}) ${goto 700}${color slate grey}Kernel:${color}${alignr 5}$kernel
${color lightgrey} ${top name 3}${goto 100}${top cpu 3}      ${goto 180}${color lightgrey} ${top_mem name 3}${goto 280}${top_mem mem 3} ${goto 350}${color slate grey}HOME:${color}${goto 390}${fs_bar 3,100 /home} ${fs_used_perc /home}% ${goto 530}(${fs_free /home} ${goto 590}/ ${fs_size /home}) ${goto 700}${color slate grey}CPU Temp:${color}${alignr 5}${hwmon temp 1}°C
$hr
${color slate grey}NET:$color ${goto 100}${upspeedgraph eth0 20,130 000000 ffffff} ${goto 350}${downspeedgraph eth0 20,130 000000 ffffff} ${goto 500}${color slate grey}CPU:${color} $cpu% ${goto 560}${cpugraph 20,130 000000 ffffff}
${voffset -20}${color}Up: ${upspeed eth0}${goto 235} ${color}Down: ${color}${downspeed eth0}${goto 500}$color(${freq_g cpu0}Ghz) ${goto 720}${color slate grey}Load: ${color }$loadavg
```


You can run as **own_window_type normal**
by changing override to normal
and uncommenting the line **#own_window_hints undecorated,below,skip_taskbar,skip_pager**

I will give it a try , but thats what you suggested yesterday or is there something different ? Thank you for your help and time .

---

### Post by Frogs Hair on 2011-05-14
This is what happens When the window type is changed to normal . :confused:

---

### Post by Frogs Hair on 2011-05-14
> **ManualSparrow said:**
> Re: Autostart
You can autostart via script by creating a blank file and renaming it conky_start in your home directory. Right-click>Permissions>Allow Executing File as a Program>Check yes.

Open the file, paste this inside:

```
#!/bin/bash
 sleep 10 && 
conky -c ~/.conkyrc;
```

Go to System>Startup Applications and click the + or Add button. Browse to the conky_start file (which should be in the home folder, path ~/conky_start) and click ok. Now this script should run on startup and after ten seconds start conky. This lets other things load first, such as compiz.
If that doesn't work and you are only using a single config file .conkyrc in the home folder, try using ```
#!/bin/bash
 sleep 10 && conky;
``` in conky_start instead. If you do want to use more than one conky (ie, start more than one conky window) you can add start them all at the same time ```
#!/bin/bash
 sleep 10 && 
conky -c ~/.conky1;
conky -c ~/.conky2;
conky -c ~/.conky3

```
etc. Just note that 
a) you need to get the path to the files right (in this case they would all be in the home folder and hidden, as per the added '.') 
b) it doesn't matter what you call the files if you use the longer versions - putting ```
conky -c PATH/TO/FILENAME
``` will start it up.

Re: compiz
If your windows are still looking goofy you can go to System Preferences>Compiz Config>Window Decorator>Rules>Add Rule>click on the running conky window>change selection to 'invert'>shadows, skip, etc. 
In this way Compiz inverts the rule and DOESN'T decorate conky.

Thank You ManulSparrow,

I went back to the page where I found the script and it was the same as the one you provided. What the person failed to write was the part about making the script executable.

Conky now starts per your instruction and I am aware that the time can be changed if needed .

---

### Post by Frogs Hair on 2011-05-14
I will mark this as solved since Conky is looking and working the way I want it to . The shadow around Conkey is not an issue , so I will override the window hints or try another script if I can find one that fits  with Unity on my monitor  . Thank You !

---

### Post by stinkeye on 2011-05-14
> **Frogs Hair said:**
> I will mark this as solved since Conky is looking and working the way I want it to . The shadow around Conkey is not an issue , so I will override the window hints or try another script if I can find one that fits  with Unity on my monitor  . Thank You !

Ok, good.
Not sure if you got this or not but
when you use 
**own_window_type normal**
you need to remove the comment symbol [COLOR="Red"]**#**[/COLOR]
from in front of 
**[COLOR="#ff0000"]#[/COLOR]own_window_hints undecorated,below,skip_taskbar,skip_pager**

or else that line won't be read and conky will have the properties of 
a normal desktop window.

---

### Post by Frogs Hair on 2011-05-14
> **stinkeye said:**
> Ok, good.
Not sure if you got this or not but
when you use 
**own_window_type normal**
you need to remove the comment symbol [COLOR="Red"]**#**[/COLOR]
from in front of 
**[COLOR="#ff0000"]#[/COLOR]own_window_hints undecorated,below,skip_taskbar,skip_pager**

or else that line won't be read and conky will have the properties of 
a normal desktop window.

Change made , Thanks Again

---

