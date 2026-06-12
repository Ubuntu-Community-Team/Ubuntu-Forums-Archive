---
title: "Conky disappear when I click on desktop"
date: 2007-05-24
forum: Desktop Effects &amp; Customization
---

### Post by kilou on 2007-05-24
Hi,

I just installed conky on my computer and I'm trying to make it work correctly on my laptop with Ubuntu 7.04 and Beryl. I've especially looked at the setting own_window_type in the conky configuration file but I can't get the right behaviour: Here is the problems depending on the parameter of own_window_type:

- own_window_type=normal: conky is correctly displayed on the desktop but when I use the scale plugin or the "see desktop" plugin in Beryl, it disappear. If I rotate the cube the conky screen is seen as a separate window, over the desktop

- own_window_type=desktop: the behaviour is perfect almost everywhere with this option except that clicking on the desktop or icon on the desktop make conky dissapear. However when this is not done conky is correctly displayed with all beryl plugin.

-own_window_type=override: here conky is also displayed as a separate window but it get the emerald shadow as well. Also when rotating the cube the conky window remains still on the screen. The conky screen always appears on top of other windows as well despite putting the argument "on_bottom yes" or below. 

- own_window no: by desactivating conky's own window, the behaviour is correct everywhere but conky flickers even if the double buffer is set to yes.

So it seems for me the best option is own_window_type=desktop but I can't understand then why as soon as I click on the desktop or any desktop icon conky disappears. Is there any way to solve that??

Thanks

PS: conky is launched with a sleep timeout script of 10 sec which seems to work well with Beryl.

---

### Post by blazercist on 2007-05-24
window type has to be override
there is another thing variable with window options it has to be set to below,undecorated

post your .conkyrc and I'll help i had the same problems.

---

### Post by kilou on 2007-05-24
Thanks for your reply blazercist. I've set the own_window_type to override and then I have increased the sleep parameter in the script that launch conky and now it seems to work OK. I guess conky was starting too early compared to Beryl/emerald and that was causing the problems with the override option. Now I have done a script to launch conky first, wait 1 sec and then launch beryl and emerald and it seems to work so far. The only remaining problem is that if I drag a desktop icon on the conky screen on the desktop, the icon disappear as it is drawn below the conky screen. Is it possible to make desktop icon be displayed on top of the conky screen??

For info here is my conkyrc:
```
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages 
# - netstat connections to your computer
#
# -- Pengo (conky@pengo.us)
#

# set to yes if you want Conky to be forked in the background
background yes

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,sticky,below,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 2.0

# Minimum size of text area
minimum_size 400 5
maximum_width 400

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
xftfont sans-10
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color A3896C

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 110

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${color}SYSTEM ${hr 2}$color
$nodename $sysname $kernel
Uptime: ${uptime}
Battery: ${battery BAT1} (${battery_time BAT1} remaining)

${color}CPU ${hr 2}$color
${freq}MHz   Temp: ${acpitemp}°C
${cpubar}$color
${cpugraph}$color
PROCESS	                         ${alignr}PID          CPU%      MEM% 
${top name 1}                    ${alignr}${top pid 1}       ${top cpu 1}       ${top mem 1}  
${top name 2}                    ${alignr}${top pid 2}       ${top cpu 2}       ${top mem 2}  
${top name 3}                    ${alignr}${top pid 3}       ${top cpu 3}       ${top mem 3}  
${top name 4}                    ${alignr}${top pid 4}       ${top cpu 4}       ${top mem 4}  
${top name 5}                    ${alignr}${top pid 5}       ${top cpu 5}       ${top mem 5}  

${color}MEMORY / DISK ${hr 2}$color 
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color

HDD Temp: ${execi 5 nc localhost 7634 | cut -c54-55 ;}°C
Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color
Home:  ${fs_free_perc /home}%   ${fs_bar 6 /home}$color

${color}NETWORK ${hr 2}$color
Ethernet (${addr eth0})
Down: $color${downspeed eth0} k/s ${downspeedgraph eth0 15,100} ${alignr}Up: ${upspeed eth0} k/s ${alignr}${upspeedgraph eth0 15,100}$color
 
WiFi (${addr eth1})
Down: $color${downspeed eth1} k/s ${downspeedgraph eth1 15,100} ${alignr}Up: ${upspeed eth1} k/s ${alignr}${upspeedgraph eth1 15,100}$color
```

---

### Post by notwen on 2007-05-24
Do you have double buffer enabled in your xorg.conf?  Check under the Module section for 

> Load    "dbe"

---

### Post by kilou on 2007-05-24
Yes it is enabled to prevent flickering.

---

### Post by blazercist on 2007-05-24
yea i have the same thing, with the icons, i dont think anything can be done about it

---

### Post by notwen on 2007-05-24
I myself do not use the Beryl 'show desktop' or 'scale' plugins, try disabling them one at a  time and see what your outcome is.  If you can narrow it down to one thing perhaps you could consult Beryl/Compiz dev teams and see if they might recommend a fix.

---

### Post by kilou on 2007-05-24
When desactivating Beryl and Emerald it is possible to set own_window_type at "desktop". Then when dragging an icon on the Conky screen, the icon is automaticall moved back to its original location on the desktop. Therefore it is not possible to place any icon on the Conky screen but at least with the desktop parameter an icon dragged on the Conky screen won't disappear, which is what we want. Now obviously the problem is that to use Conky with Bery we must use the "override" parameter to own_window_type because when using "desktop", conky disappears as soon as the desktop is clicked or an icon is selected.

But I'm thinking about a workaround to this: is it possible to tell Ubuntu, nautilus or X  that it is not possible to move any icon in a particular region of the desktop?? This would be like a script run at startup that would block the area where  conky is displayed and prevent any icon to be moved there??? Do you think this is possible to do? (this should only apply to the desktop icons but not to windows)

---

### Post by orb9220 on 2007-05-24
Fixed mine by changing to this in conky file.

> own_window yes
own_window_transparent yes
own_window_type root
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes


and 

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
**    Load           "dbe"**
    Load           "dri"

Load "dbe" in my xorg for nvidia don't know for others.

---

### Post by kilou on 2007-05-24
When I use "own_window_type root" I get an error and conky starts with own_window_type normal so it makes no difference on my system. Desktop icons are not hidden behind conky only if either Beryl is not running or if double buffering is disabled (which causes conk to flicker).

So it seems that with Beryl running there are still some incompatibilities :(

---

### Post by orb9220 on 2007-05-24
Are you running nvidia or?

---

### Post by kilou on 2007-05-25
No Nvidia or ATi. I have a i915GMA with AIGLX.

---

### Post by kilou on 2007-05-25
Is it possible to use Devilspie to put the conky screen "below" the desktop icons so that those get displayed on top of conky?? Also would it be possible to use Devilspie to allow conky to start properly with Beryl (without having to launch conky with a startup script with the sleep command)???

---

### Post by Bill Cosby on 2007-06-15
Hey there, I have the same problem, except when I use "override", conky doesn't show up at all, with "normal" I get the shadows, and with "desktop" it disappears when I cklick on the desktop, any solutions?

I have the dbe module, double buffering is enabled and I use the binary nvidia drivers for my nvidia card :)
I don't use berryl though, I use the xcompmgr and openbox as a wm in gnome, but even if I kill it, I don't get conky with override (then normal works though, since there are no shadows anymore :))

Right now I can choose between conky or shadows :( but shadows are nice, and so is conky

Thanks in advance

---

### Post by Dermis on 2008-05-08
> **kilou said:**
> No Nvidia or ATi. I have a i915GMA with AIGLX.

try to set **background no**

and it works for me using i915GMA

:guitar:

---

