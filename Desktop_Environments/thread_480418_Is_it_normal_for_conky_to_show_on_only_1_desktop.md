---
title: "Is it normal for conky to show on only 1 desktop?"
date: 2007-06-21
forum: Desktop Environments
---

### Post by timzak on 2007-06-21
I just started playing with conky last night and noticed it only shows on my primary desktop (I use Beryl...didn't notice if conky does the same in Metacity).  Is this normal for conky?  Or should it be showing on all 4 sides of the cube?

Thanks.

---

### Post by Happy_Man on 2007-06-21
It should.... it generally doesn't...... don't use conky, so can't help much more... sorry.

---

### Post by orb9220 on 2007-06-21
Post your .conkyrc here for help.

---

### Post by diatribe on 2007-06-21
theres a setting in the .conkyrc file to set it as sticky, I forget what though

---

### Post by timzak on 2007-06-22
> **orb9220 said:**
> Post your .conkyrc here for help.

```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar
background no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 400 5

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

# Default colors and also border colors, grey90 == #e5e5e5
default_color white
default_shade_color black
default_outline_color white

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale no
xftfont Terminus:size=8
xftalpha 0.8

TEXT

${offset 240}${color slate grey}${time %a, } ${color }${time %e %B %G}
${offset 240}${color slate grey}${time %Z,    }${color }${time %H:%M:%S}
${offset 240}${color slate grey}UpTime: ${color }$uptime
${offset 240}${color slate grey}Kern: ${color }$kernel
${offset 240}${color slate grey}Freq: ${color }${freq_g} Ghz
${offset 240}${color slate grey}CPU: ${color } $cpu%  ${acpitemp} C
${offset 240}${cpugraph 20,130 000000 ffffff}
${offset 240}${color slate grey}Load: ${color }$loadavg
${offset 240}${color slate grey}Processes: ${color }$processes  
${offset 240}${color slate grey}Running:   ${color }$running_processes

${offset 240}${color slate grey}Highest CPU:
${offset 240}${color #ddaa00} ${top name 1}${top_mem cpu 1}
${offset 240}${color lightgrey} ${top name 2}${top cpu 2}
${offset 240}${color lightgrey} ${top name 3}${top cpu 3}
${offset 240}${color lightgrey} ${top name 4}${top cpu 4}

${offset 240}${color slate grey}Highest MEM:
${offset 240}${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${offset 240}${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${offset 240}${color lightgrey} ${top_mem name 3}${top_mem mem 3}
${offset 240}${color lightgrey} ${top_mem name 4}${top_mem mem 4}

${offset 240}${color slate grey}MEM:  ${color } $memperc% $mem/$memmax
${offset 240}${membar 3,100}
${offset 240}${color slate grey}SWAP: ${color }$swapperc% $swap/$swapmax
${offset 240}${swapbar 3,100}

${offset 240}${color slate grey}HOME:  ${color }${fs_free /home}/${fs_size /home}
${offset 240}${fs_bar 3,100 /home}
${offset 240}${color slate grey}SLACK:  ${color }${fs_free /mnt/slack}/${fs_size /mnt/slack}
${offset 240}${fs_bar 3,100 /mnt/slack}
${offset 240}${color slate grey}NET: 
${offset 240}${color}Up: ${color }${upspeed eth0} k/s
${offset 240}${upspeedgraph eth0 20,130 000000 ffffff}
${offset 240}${color}Down: ${color }${downspeed eth0}k/s${color}
${offset 240}${downspeedgraph eth0 20,130 000000 ffffff}
```

Thanks.  So my main question again is, how to get conky to show on all 4 workspaces/cube sides.  I do have a second question.  if acpitemp doesn't work (it shows 0 C), is there any other way to get cpu temp to show?

---

### Post by timzak on 2007-06-22
*bump*...I posted my conky file, can someone take a peek?

Thanks.

---

### Post by orb9220 on 2007-06-23
[Howto Install and Configure lm-sensors]("http://ubuntuforums.org/showthread.php?t=2780&highlight=lm-sensors")
[Howto: Get a beautiful Conky 1.4.2 setup]("http://ubuntuforums.org/showthread.php?t=205865&highlight=lm-sensors")

---

### Post by timzak on 2007-06-24
Thanks, when you asked me to post my conky file, I thought I'd get individualized help.  I've already read through both of those threads and haven't found anything specifically related to having conky show on all 4 sides of a Beryl cube.  I tried ```
own_window_type desktop
``` on my own, based on reading through the conky homepage.  This actually caused conky to appear on all 4 sides of the cube, but it was invisible except for when I activated the cube with my middle mouse button.  So when I'm spinning the cube, I can see conky on all 4 sides but when I select a workspace, conky disappears.  If I remark out the above code, I see conky great on workspace 1, but it doesn't show on the other faces of the cube.

Any other ideas?

---

### Post by orb9220 on 2007-06-24
My nvidia xorg Module section

> Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
    **Load           "dbe"**
    Load           "dri"

Had to add to my xorg Load dbe to it for conky,

My relevant .conkyrc section

> # Create own window instead of using desktop (required in nautilus)
#own_window no
#own_window yes
#own_window_type override
#own_window_transparent 1

own_window yes
own_window_transparent yes
own_window_type root
#own_window_hints below sticky undecorated
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer Yes

If in the begining of post if you would have stated what you already tried and that you read thru threads I could have been more specific in providing help.

---

### Post by orb9220 on 2007-06-24
> if acpitemp doesn't work (it shows 0 C),

Did you install lm-sensors?

Then you have to open a term and **sudo sensors-detect**
answer yes to all prompts. 

Then open modules file **/etc/modprobe.d/modules** and put a comment # in front of eeprom to # eeprom save file.

My  .conkyrc ends up with for temps and fans.
> 
TEXT
${offset 10}${color }UpTime: ${color }$uptime
${offset 10}${color }Kern:${color }$kernel

${offset 10}${color #ddaa00}CPU:${color } $cpu%
${offset 10}${cpugraph 20,100 000000 ffffff}
${offset 10}Athlon 64 3500+
${offset 10}@ ${freq_g} GHz

${offset 10}${color #ddaa00}Cpu Temp: ${color white}$**{i2c tempf 2} **F
${offset 10}${color #ddaa00}Cpu Fan: ${color white}$**{i2c fan 2}** rpm

${offset 10}${color #ddaa00}M/B Temp: ${color white}${i2c tempf 1} F
${offset 10}${color #ddaa00}M/B Fan: ${color white}${i2c fan 1} rpm

${offset 10}${color #ddaa00}Disk I/O: $color${diskio}
${offset 10}${diskiograph 20,100 000000 ffffff}
${offset 10}${color #ddaa00}Load: ${color white}${loadavg}
${offset 10}${color #ddaa00}Processes: ${color }$processes  

${offset 10}${color #ddaa00}MEM:  ${color } $memperc% $mem
${offset 10}${membar 3,100}
${offset 10}${color #ddaa00}SWAP: ${color }$swapperc% $swap
${offset 10}${swapbar 3,100}

${offset 10}${color #ddaa00}ROOT:    ${color }${fs_free /}
${offset 10}${fs_bar 3,100 /}
${offset 10}${color #ddaa00}HOME:  ${color }${fs_free /home}
${offset 10}${fs_bar 3,100 /home}
${offset 10}${color #ddaa00}114GB:  ${color }${fs_free /home/orb/Drives/114GB}
${offset 10}${fs_bar 3,100 /home/orb/Drives/114GB}
${offset 10}${color #ddaa00}NET: 
${offset 10}${color}Up: ${color }${upspeedf ath0} kB/s
${offset 10}${upspeedgraph ath0 20,100 000000 ffffff}
${offset 10}${color}Down: ${color }${downspeedf ath0}kB/s${color}
${offset 10}${downspeedgraph ath0 20,100 000000 ffffff}
${offset 10}${color}Link Status: ${color }${linkstatus ath0}
${offset 10}${color}IP: ${addr ath0}

As it shows for my mobo I had to use i2c which sudo sensors-detect showed me during probing. Yours may differ you have to determine if acpi is for yours or 12c.

Hope this helps

---

### Post by timzak on 2007-06-24
Thanks for your help.  I remarked out my statements in conky and replaced them with yours, and I already had "dbe" set in my xorg.conf file.  Unfortunately, I still only get conky showing on workspace 1.  I'm not sure what else to try.  I'll try your help on the sensors when I get a chance.  I'm not as concerned with that as with getting conky working on all 4 workspaces.  Any other ideas?  I'll try and be more specific in future posts about what I've already tried.

Thanks.

---

### Post by timzak on 2007-06-25
Update:  conky actually shows on all 4 workspaces when Beryl is inactive.  But if I change Window Managers to Beryl, conky only shows on the workspace that was active when I switched the Window Manager.  So at the moment, I was on workspace 3 when I switched (via Beryl Manager) from Metacity to Beryl, and now conky shows on workspace 3, but no other workspace.

So is anyone getting conky working on all 4 workspaces with Beryl?

---

### Post by timzak on 2007-06-26
Just wanted to close this thread as resolved.  orb9220 was kind enough to supply a solution via private message:

> open gedit and paste below and save it as .conky-start.sh
Quote:
#!/bin/bash
sleep 10 && conky ;
Makes sure to make it executable by righ-click properties and selecting make executable.

Also don't forget to remove conky from session startup and add .conky-startup.sh instead to autostartup programs in session manager.


This basically tells conky to wait 10 seconds after Beryl loads before loading itself.  Voila!  conky now shows on all 4 sides of a Beryl cube.

My thanks to orb for his/her help.

---

### Post by orb9220 on 2007-06-26
And they say the Blind leading the Blind doesn't work! 

Glad you got it working.

---

### Post by ncappel1 on 2007-12-22
just wanted to say that this post helped me do the opposite, I was trying to find out how to make conky only be present on a single workspace. thanks!

---

