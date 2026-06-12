---
title: "conky problem"
date: 2010-08-02
forum: Desktop Environments
---

### Post by mesaphlin on 2010-08-02
Hello everyone,

I just downloaded conky and did some .conkyrc stuff (I don't know what I did actually) :P

And now everytime, I write conky in the terminal,

it spits out...

pil@Pil:~$ conky
Conky: missing text block in configuration; exiting
***** Imlib2 Developer Warning ***** :
    This program is calling the Imlib call:

    imlib_context_free();

    With the parameter:

    context

    being NULL. Please fix your program.


Please help me!!!... what should I do the run the conky?

Thanks in advance...

:(

---

### Post by Maverick_Meerkat on 2010-08-02
Greetings, 

I am rather new to Ubuntu and Conky, but it seems there is a problem with Conky locating or configuring the text output section of the conkyrc file.

Is your conkyrc file hidden? Is it named ".conkyrc" and is it located in your /home/yourusername directory. 

You can try swapping .conkyrc files to test if a different one works. If so, you can compare the two files to see if yours is missing any important entries. Perhaps you deleted or commented out a line you shouldn't have.

Try using this script it works for me and is easy to read. 

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

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer right
use_xft no

# Update interval in seconds
update_interval 5.5

# Min/Max size of text area
minimum_size 250 5
maximum_width 180

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
uppercase yes # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
# border_margin 9

# border width
border_width 10

# Default colors and also border colors
default_color magenta

own_window_colour black
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

temperature_unit fahrenheit

#THIS IS THE TEXT BLOCK AND SEEMS TO BE THE SOURCE OF THE ERROR
# stuff after &#8216;TEXT&#8217; will be formatted on screen
TEXT


${color green}
SYSTEM ${color blue}${hr 2}${color}
$nodename Lucid Lynx 10.04
$sysname $kernel $machine ${color green}

CPU ${color blue}${hr 2}$color
Intel Celeron M-360 ${alignr}${freq_g cpu0}Ghz

MHz    ${color grey}${freq} ${alignr}${color} Temp ${color grey}${acpitemp}*f${color}
Usage  ${color grey}${cpu cpu0}% ${color red}$cpubar${color green}

MEMORY ${color blue}${hr 2}$color
Total  ${color grey}$memmax ${color}
Used   ${color grey}$mem ${color}
Free   ${color grey}$memeasyfree ${color}
RAM    ${color grey}$memperc% ${color orange}${membar 6}${color green}

Drive ${color blue}${hr 2}$color
Total  ${color grey}${fs_size} ${color}
Used   ${color grey}${fs_used}${color}
Free   ${color grey}${fs_free}${color}
Usage  ${color grey}${fs_used_perc /}% ${color yellow}${fs_bar 6 /}${color}${color green}
#XP Pro ${color grey}${fs_used_perc /media/XP Pro}% ${color yellow}${fs_bar 6 /media/XP Pro}${color}
#Data   ${color grey}${fs_used_perc /media/Data}% ${color yellow}${fs_bar 6 /media/Data}}${color green}

Procs ${color blue}${hr 2}$color
NAME               CPU%   MEM% ${color grey}
${top name 1} ${top cpu 1} ${top mem 1}
${top name 2} ${top cpu 2} ${top mem 2}
${top name 3} ${top cpu 3} ${top mem 3}
${top name 4} ${top cpu 4} ${top mem 4}${color green}

NETWORK ${color blue}${hr 2}${color}
Address  ${color grey}${addr wlan0}${color}
Bitrate  ${color grey}${wireless_bitrate wlan0}${color}

WLan Qt  ${color grey}${wireless_link_qual_perc wlan0}% ${color green}${wireless_link_bar 6 wlan0}${color}

Down ${color grey}${downspeed wlan0}${color}
${downspeedgraph wlan0 50 00ff00} ${color}
Up   ${color grey}${upspeed wlan0}${color}
${upspeedgraph wlan0 50 00ff00}${color}
Recv ${color grey}${totaldown wlan0} ${color}${alignr}Sent ${color grey}${totalup wlan0}${color}
NIBC ${color grey}${tcp_portmon 1 32767 count}      ${color}NOBC ${color grey}${tcp_portmon 32768
61000 count} ${color}${alignr}Total ${color grey}${tcp_portmon 1 65535 count}
${color blue}${hr 2}
#
#END OF SCRIPT I AM USING
#
#${color orange}LOGGING ${hr 2}$color
#${execi 30 tail -n3 /var/log/messages | fold -w50}
```

---

### Post by mesaphlin on 2010-08-02
Dear Maverick_Meerkat,

Thank you so much!!!...

It works perfectly now...

I have also one question...

What should I do if I want the Conky starts immediately when I open the computer without writing the conky in the terminal?

I thank you so much for your help !!!!....

:guitar:

---

### Post by Maverick_Meerkat on 2010-08-02
> **mesaphlin said:**
> 
What should I do if I want the Conky starts immediately when I open the computer without writing the conky in the terminal?
:guitar:

1. In the desktop drop down menu navigate System>Preferences>Startup Applications

2. Click the add button.

3. Enter conky in every empty field.

NOTE: This may or may not work properly! Some users report that Conky appears only to be hidden behind the desktop. In that case we need to use a small script to delay Conky from starting until after nautilus has loaded into memory. See [http://ubuntuforums.org/archive/index.php/t-386078.html](http://ubuntuforums.org/archive/index.php/t-386078.html)
for more info on that.

Alternately, you can create a shortcut/launcher using the menu editor. Then all you need is to click the icon and Conky is up and running at the push of a button.

---

### Post by mesaphlin on 2010-08-02
Thank you so much!!!...

;)=D>

---

