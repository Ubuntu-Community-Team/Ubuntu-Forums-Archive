---
title: "Conky help: how can I create rounded borders"
date: 2009-12-07
forum: Desktop Environments
---

### Post by Blackie_Chan on 2009-12-07
Hi All, 

I've attached an image of my conky on desktop, all it has is the weather. How can I make the conky border rounded (instead of squared)?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=138889&stc=1&d=1260162729[/IMG]

My .conkyrc
```
# conky configuration

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
xftfont Bitstream Vera Sans Mono:size=10

# Text alpha when using Xft
xftalpha 0.8

# Update interval in seconds
update_interval 1.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
#own_window no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 300 0
maximum_width 500

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline yes

# Draw borders around text
draw_borders no
draw_graph_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 10

# border width
border_width 1

# Default colors and also border colors
default_color F8F8FF
default_shade_color black
default_outline_color black

# own window options
own_window		yes
own_window_transparent  no 
own_window_type		override
own_window_colour       black 
own_window_hints	decorated,below,sticky,skip_taskbar

# Text alignment, other possible values are commented
alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 10
gap_y 10

# set to yes if you want all text to be in uppercase
uppercase no

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer right

# colours
color1 white
# light blue
color2 6892C6
# orange
color3 FC8820
# green
color4 78BF39
# red
color5 CC0000

text_buffer_size 2048

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT
${offset -5}${color3}WEATHER ${voffset -2}${hr}${color1}
${voffset 20}${goto 5}${font ConkyWeather:style=Bold:size=80}${execpi 3600 $HOME/.conky/getField.sh Image}${font}
${voffset -100}${goto 140}${color1}${font Zekton:size=25}${execpi 3600 $HOME/.conky/getField.sh Temperature}${font}
${voffset 10}${goto 140}${color1}${font Bitstream Vera Sans Mono:size=12}${execpi 3600 $HOME/.conky/getField.sh Conditions}${font}
${voffset 10}${goto 140}${color3}Feels Like: ${color1}${execpi 3600 $HOME/.conky/getField.sh Feels}
${goto 140}${color3}Wind: ${color1}${execpi 3600 $HOME/.conky/getField.sh Wind}
${goto 140}${color3}Humidity: ${color1}${execpi 3600 $HOME/.conky/getField.sh Humidity}
${color3}${voffset 5}${hr}

${goto 90}${color3}${execpi 3600 $HOME/.conky/getField.sh POT1}
${goto 80}${voffset 10}${color1}${font ConkyWeather:size=40}${execpi 3600 $HOME/.conky/getField.sh Header1_Cond}${font}
${goto 100}${voffset 10}${execpi 3600 $HOME/.conky/getField.sh Header1_Temp}

${goto 175}${voffset -125}${color3}${execpi 3600 $HOME/.conky/getField.sh POT2}
${goto 165}${voffset 10}${color1}${font ConkyWeather:style=Bold:size=40}${execpi 3600 $HOME/.conky/getField.sh Header2_Cond}${font}
${goto 180}${voffset 10}${execpi 3600 $HOME/.conky/getField.sh Header2_Temp}

${goto 260}${voffset -125}${color3}${execpi 3600 $HOME/.conky/getField.sh POT3}
${goto 250}${voffset 10}${color1}${font ConkyWeather:style=Bold:size=40}${execpi 3600 $HOME/.conky/getField.sh Header3_Cond}${font}
${goto 270}${voffset 10}${execpi 3600 $HOME/.conky/getField.sh Header3_Temp}

${goto 5}${color3}POP:
${goto 5}${color3}Snow:

${goto 95}${voffset -50}${color1}${execpi 3600 $HOME/.conky/getField.sh Header1_Pop}
${goto 95}${voffset 5}${color1}${execpi 3600 $HOME/.conky/getField.sh Header1_snow}

${goto 175}${voffset -55}${color1}${execpi 3600 $HOME/.conky/getField.sh Header2_Pop}
${goto 175}${voffset 5}${color1}${execpi 3600 $HOME/.conky/getField.sh Header2_snow}

${goto 270}${voffset -55}${color1}${execpi 3600 $HOME/.conky/getField.sh Header3_Pop}
${goto 270}${voffset 5}${color1}${execpi 3600 $HOME/.conky/getField.sh Header3_snow}

```

---

### Post by stinkeye on 2009-12-07
If you are using conky version 1.71 or above with lua and cairo enabled
you can use this script
[_[COLOR="DarkRed"]Background Colour with Lua/Cairo[/COLOR]_]("http://conky.linux-hardcore.com/?page_id=3002")
[COLOR="DarkRed"]Edit[/COLOR]: If you have problems downloading the file from linux-hardcore It's attached below.

To check your conky version in terminal
```
conky -v
```
and the last few  lines should look look like this...
```
 Lua bindings:
   * Cairo
   * Imlib2

```
If not you'll need to uninstall conky and install the conky-all version through synaptic.
The first part of the script tells you how to use it.
Just paste those two lines above "TEXT" in your conky config, setting the path to where you put the script.
and make sure you have 
```
own_window_transparent yes
```

This is my conky config above "TEXT" for the bottom conky in the pic.
You may have to add or fiddle with the settings highlighted.
```
background yes
update_interval 30
total_run_times 0

use_xft yes
xftfont GE Inspira:bold:size=10
alignment tr
xftalpha 1.0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10

default_shade_color grey
default_outline_color black
default_color 919FAA
use_spacer none
no_buffers yes
uppercase no
color1 F8DF58
[COLOR="#8b0000"]text_buffer_size 4096[/COLOR]
[COLOR="#8b0000"]max_specials 1024[/COLOR]
[COLOR="#8b0000"]max_user_text 4000[/COLOR]
override_utf8_locale yes
minimum_size 540 
maximum_width 540 
gap_x 25
gap_y 825
border_inner_margin 5
border_outer_margin 6

lua_load /home/glen/conky/draw_bg.lua
lua_draw_hook_pre draw_bg
[COLOR="Red"]imlib_cache_size 0[/COLOR]

TEXT
```

---

