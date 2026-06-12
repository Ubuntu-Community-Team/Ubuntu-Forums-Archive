---
title: "How to change conky font size?"
date: 2010-02-10
forum: Desktop Environments
---

### Post by vickoxy on 2010-02-10
Hi,
i use this simple conky script, but i like font and want to add the clock and the date with the bigger fonts-but i can not do it.

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
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft no

# Update interval in seconds
update_interval 1.0

# Minimum size of text area
minimum_size 186 0
maximum_width 220 0

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
#use_xft yes
xftfont Samanata
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color ace770

own_window_colour black
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 20


#${color blue}FORTUNE ${hr 2}$color
#${execi 120 fortune -s | fold -w50}


#${color blue}LOGGING ${hr 2}$color
#${execi 30 tail -n3 /var/log/messages | fold -w50}



# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${color #5397d6}SYSTEM ${hr 2}$color
${voffset 4}UpTime: ${alignr}${color }$uptime
${voffset 2}Kern: ${alignr}$kernel
${voffset 2}CPU: ${cpu}% ${alignr 1}${cpubar 6,80}
${cpugraph 000000 ffffff}
Intel Atom N270 ${alignr} ${alignr}${freq}MHz   ${acpitemp}C
${voffset 2}RAM: $memperc% ${alignc} $mem${alignr 7} ${membar 6,80}
${voffset 2}${alignc -44}CPU%	${alignr}MEM%
${voffset 2}${top_mem name 1}${alignr}${top_mem cpu 1}   ${top_mem mem 1}
${voffset 2}${top_mem name 2}${alignr}${top_mem cpu 2}   ${top_mem mem 2}
${voffset 2}${top_mem name 3}${alignr}${top_mem cpu 3}   ${top_mem mem 3}
${voffset 2}${top_mem name 4}${alignr}${top_mem cpu 4}   ${top_mem mem 4}
${voffset 6}${color #5397d6}STORAGE ${hr 2}$color
${voffset 2}HD: ${voffset 0}${fs_free /home}/${fs_size /home} ${alignr 1}${fs_bar 6,50 /home}
${if_mounted /media/DATA}${voffset 2}SD/USB: ${voffset 0}${fs_free /media/DATA}/${fs_size /media/DATA} ${alignr}${fs_bar 6,50 /media/DATA}${endif}
${color #5397d6}NETWORK ${hr 2}$color
${voffset 2}Upload: ${alignr}${upspeedf eth2} KB/s
${voffset 2}Download: ${alignr}${downspeedf eth2} KB/s
```

If i uncheck 
```
#use_xft yes
```

then i have bigger fonts-i can change size, but that some totally different font, and i want default one. Is something like this possible?

---

### Post by stinkeye on 2010-02-10
Conky defaults to a font size of 8, unless you specify in your config.

Change```
xftfont Samanata
```
to
```
xftfont Samanata:size=10
```
or whatever size you want.

You can also change different parts of your conky to use different fonts by using for example
```
${font LCDMono:bold:size=12}
or
${font GE Inspira:size=10}
```
in front of the part you want change.
It will continue using that font until you change to another font or you
go back to your xftfont by adding ```
${font}
```

---

### Post by vickoxy on 2010-02-10
Default size is ok, but i want to add these two lines with bigger fonts:

```
${alignc 60}${font Arial Black:size=26}${time %H:%M:%S}${font}
${alignc}${time %A, %d.%m.%Y}
```

But no metter what i do the font size is not changed. As soon as i change
```
#use_xft yes
```
to
```
use_xft yes
```

i got bigger fonts, but also totally another font.

---

### Post by vickoxy on 2010-02-10
> **stinkeye said:**
> Conky defaults to a font size of 8, unless you specify in your config.

Change```
xftfont Samanata
```
to
```
xftfont Samanata:size=10
```
or whatever size you want.

You can also change different parts of your conky to use different fonts by using for example
```
${font LCDMono:bold:size=12}
or
${font GE Inspira:size=10}
```
in front of the part you want change.
It will continue using that font until you change to another font or you
go back to your xftfont by adding ```
${font}
```

I added this line:
```
${font LCDMono:bold:size=12}${time %H:%M:%S}${font}
```

but no changes are visable

---

### Post by stinkeye on 2010-02-10
Try
```
${alignc 60}${font [COLOR="DarkRed"]Samanata[/COLOR]:size=26}${time %H:%M:%S}${font}
${alignc}${time %A, %d.%m.%Y}
```

What I gave you previously was examples of how to change font and sizes.
You have to have those fonts for them to display.
A google search "font xxxxx" will find most fonts or go to [**_[COLOR="DarkRed"]dafont[/COLOR]_**]("http://www.dafont.com/").

Put any downloaded fonts in your home directory in a folder named ".fonts"
[COLOR="DarkRed"]*Note[/COLOR] the dot at the front makes it a hidden file.
Create a .fonts folder if you don't have one.
When in nautilus file browser ctrl + h will show hidden files and folders.

---

### Post by vickoxy on 2010-02-10
> **stinkeye said:**
> Try
```
${alignc 60}${font [COLOR="DarkRed"]Samanata[/COLOR]:size=26}${time %H:%M:%S}${font}
${alignc}${time %A, %d.%m.%Y}
```

Unfortunately-nothing happens-no size change.

---

### Post by vickoxy on 2010-02-10
> **stinkeye said:**
> Try
```
${alignc 60}${font [COLOR="DarkRed"]Samanata[/COLOR]:size=26}${time %H:%M:%S}${font}
${alignc}${time %A, %d.%m.%Y}
```

What I gave you previously was examples of how to change font and sizes.
You have to have those fonts for them to display.
A google search "font xxxxx" will find most fonts or go to [**_[COLOR="DarkRed"]dafont[/COLOR]_**]("http://www.dafont.com/").

Put any downloaded fonts in your home directory in a folder named ".fonts"
[COLOR="DarkRed"]*Note[/COLOR] the dot at the front makes it a hidden file.
Create a .fonts folder if you don't have one.
When in nautilus file browser ctrl + h will show hidden files and folders.
Well, i have those fonts-i said-if i change
Code:
#use_xft yes
to
Code:
use_xft yes

i can manage font sizes as here described-but i have no more this default font. And have no ide what is ```
use_xft yes
``` and why it allows me to change font (but not to use defaulr samanata)

---

### Post by stinkeye on 2010-02-10
This is how your conky looks on my computer using```
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
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes


# Update interval in seconds
update_interval 1.0

# Minimum size of text area
minimum_size 186 0
maximum_width 220 0

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
use_xft yes
xftfont Samanata
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color ace770

own_window_colour black
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 20


#${color blue}FORTUNE ${hr 2}$color
#${execi 120 fortune -s | fold -w50}


#${color blue}LOGGING ${hr 2}$color
#${execi 30 tail -n3 /var/log/messages | fold -w50}



# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${color #5397d6}SYSTEM ${hr 2}$color
${voffset 4}UpTime: ${alignr}${color }$uptime
${voffset 2}Kern: ${alignr}$kernel
${voffset 2}CPU: ${cpu}% ${alignr 1}${cpubar 6,80}
${cpugraph 000000 ffffff}
Intel Atom N270 ${alignr} ${alignr}${freq}MHz   ${acpitemp}C
${voffset 2}RAM: $memperc% ${alignc} $mem${alignr 7} ${membar 6,80}
${voffset 2}${alignc -44}CPU%	${alignr}MEM%
${voffset 2}${top_mem name 1}${alignr}${top_mem cpu 1}   ${top_mem mem 1}
${voffset 2}${top_mem name 2}${alignr}${top_mem cpu 2}   ${top_mem mem 2}
${voffset 2}${top_mem name 3}${alignr}${top_mem cpu 3}   ${top_mem mem 3}
${voffset 2}${top_mem name 4}${alignr}${top_mem cpu 4}   ${top_mem mem 4}
${voffset 6}${color #5397d6}STORAGE ${hr 2}$color
${voffset 2}HD: ${voffset 0}${fs_free /home}/${fs_size /home} ${alignr 1}${fs_bar 6,50 /home}
${if_mounted /media/DATA}${voffset 2}SD/USB: ${voffset 0}${fs_free /media/DATA}/${fs_size /media/DATA} ${alignr}${fs_bar 6,50 /media/DATA}${endif}
${color #5397d6}NETWORK ${hr 2}$color
${voffset 2}Upload: ${alignr}${upspeedf eth2} KB/s
${voffset 2}Download: ${alignr}${downspeedf eth2} KB/s
${alignc 60}${font Samanata:size=26}${time %H:%M:%S}${font}
${alignc}${time %A, %d.%m.%Y}
```

The Samanata font is in the package
```
ttf-devanagari-fonts
```
Which you can download through synaptic package manager.
Once downloaded enter 
```
fc-cache -vf
```
in the terminal to refresh the font cache.

---

### Post by vickoxy on 2010-02-10
Picture one with this code:

```
# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
#use_xft yes
xftfont Samanata
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color ace770

own_window_colour black
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 20


#${color blue}FORTUNE ${hr 2}$color
#${execi 120 fortune -s | fold -w50}


#${color blue}LOGGING ${hr 2}$color
#${execi 30 tail -n3 /var/log/messages | fold -w50}



# stuff after 'TEXT' will be formatted on screen

TEXT
${alignc}${font times:size=26}${time %H:%M:%S}${font}
${alignc}${time %A, %d.%m.%Y}
$color
${color #5397d6}SYSTEM ${hr 2}$color
${voffset 4}UpTime: ${alignr}${color }$uptime
${voffset 2}Kern: ${alignr}$kernel
${voffset 2}CPU: ${cpu}% ${alignr 1}${cpubar 6,80}
${cpugraph 000000 ffffff}
Intel Atom N270 ${alignr} ${alignr}${freq}MHz   ${acpitemp}C
${voffset 2}RAM: $memperc% ${alignc} $mem${alignr 7} ${membar 6,80}
${voffset 2}${alignc -44}CPU%	${alignr}MEM%
${voffset 2}${top_mem name 1}${alignr}${top_mem cpu 1}   ${top_mem mem 1}
${voffset 2}${top_mem name 2}${alignr}${top_mem cpu 2}   ${top_mem mem 2}
${voffset 2}${top_mem name 3}${alignr}${top_mem cpu 3}   ${top_mem mem 3}
${voffset 2}${top_mem name 4}${alignr}${top_mem cpu 4}   ${top_mem mem 4}
${voffset 6}${color #5397d6}STORAGE ${hr 2}$color
${voffset 2}HD: ${voffset 0}${fs_free /home}/${fs_size /home} ${alignr 1}${fs_bar 6,50 /home}
${if_mounted /media/DATA}${voffset 2}SD/USB: ${voffset 0}${fs_free /media/DATA}/${fs_size /media/DATA} ${alignr}${fs_bar 6,50 /media/DATA}${endif}
${color #5397d6}NETWORK ${hr 2}$color
${voffset 2}Upload: ${alignr}${upspeedf eth2} KB/s
${voffset 2}Download: ${alignr}${downspeedf eth2} KB/s
```

The i only change in picture two:
```
#use_xft yes
```
to
```
use_xft yes
```

```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft no

# Update interval in seconds
update_interval 1.0

# Minimum size of text area
minimum_size 186 0
maximum_width 220 0

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
use_xft yes
xftfont Samanata
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color ace770

own_window_colour black
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 20


#${color blue}FORTUNE ${hr 2}$color
#${execi 120 fortune -s | fold -w50}


#${color blue}LOGGING ${hr 2}$color
#${execi 30 tail -n3 /var/log/messages | fold -w50}



# stuff after 'TEXT' will be formatted on screen

TEXT
${alignc}${font times:size=26}${time %H:%M:%S}${font}
${alignc}${time %A, %d.%m.%Y}
$color
${color #5397d6}SYSTEM ${hr 2}$color
${voffset 4}UpTime: ${alignr}${color }$uptime
${voffset 2}Kern: ${alignr}$kernel
${voffset 2}CPU: ${cpu}% ${alignr 1}${cpubar 6,80}
${cpugraph 000000 ffffff}
Intel Atom N270 ${alignr} ${alignr}${freq}MHz   ${acpitemp}C
${voffset 2}RAM: $memperc% ${alignc} $mem${alignr 7} ${membar 6,80}
${voffset 2}${alignc -44}CPU%	${alignr}MEM%
${voffset 2}${top_mem name 1}${alignr}${top_mem cpu 1}   ${top_mem mem 1}
${voffset 2}${top_mem name 2}${alignr}${top_mem cpu 2}   ${top_mem mem 2}
${voffset 2}${top_mem name 3}${alignr}${top_mem cpu 3}   ${top_mem mem 3}
${voffset 2}${top_mem name 4}${alignr}${top_mem cpu 4}   ${top_mem mem 4}
${voffset 6}${color #5397d6}STORAGE ${hr 2}$color
${voffset 2}HD: ${voffset 0}${fs_free /home}/${fs_size /home} ${alignr 1}${fs_bar 6,50 /home}
${if_mounted /media/DATA}${voffset 2}SD/USB: ${voffset 0}${fs_free /media/DATA}/${fs_size /media/DATA} ${alignr}${fs_bar 6,50 /media/DATA}${endif}
${color #5397d6}NETWORK ${hr 2}$color
${voffset 2}Upload: ${alignr}${upspeedf eth2} KB/s
${voffset 2}Download: ${alignr}${downspeedf eth2} KB/s
```

See: in picture two-times (clock) is recognized, but i lost default font and size is too big

---

### Post by vickoxy on 2010-02-10
Ok, so it seems that i have no samanata-and i do not know what is this default font called-that i have in conky on picture 1...

---

### Post by stinkeye on 2010-02-10
In your conky you have 2 occurrences of use_xft .
Delete the  use_xft no.

---

### Post by stinkeye on 2010-02-10
Basically you can use any font you like.
Open up Appearance > fonts and choose what you like and change any instances of Samanata in your conky with a font you like.

---

### Post by stinkeye on 2010-02-10
Just use this
```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes


# Update interval in seconds
update_interval 1.0

# Minimum size of text area
minimum_size 186 0
maximum_width 220 0

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
use_xft yes
xftfont Sans:size=8
xftalpha 0.8

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3



# Default colors and also border colors, grey90 == #e5e5e5
default_color ace770

own_window_colour black
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 20


#${color blue}FORTUNE ${hr 2}$color
#${execi 120 fortune -s | fold -w50}


#${color blue}LOGGING ${hr 2}$color
#${execi 30 tail -n3 /var/log/messages | fold -w50}



# stuff after 'TEXT' will be formatted on screen

TEXT
${font Sans:size=26}${alignc}${time %H:%M:%S}${font}
${alignc}${time %A, %d.%m.%Y}
$color
${color #5397d6}SYSTEM ${hr 2}$color
${voffset 4}UpTime: ${alignr}${color }$uptime
${voffset 2}Kern: ${alignr}$kernel
${voffset 2}CPU: ${cpu}% ${alignr 1}${cpubar 6,80}
${cpugraph 000000 ffffff}
Intel Atom N270 ${alignr} ${alignr}${freq}MHz   ${acpitemp}C
${voffset 2}RAM: $memperc% ${alignc} $mem${alignr 7} ${membar 6,80}
${voffset 2}${alignc -44}CPU%	${alignr}MEM%
${voffset 2}${top_mem name 1}${alignr}${top_mem cpu 1}   ${top_mem mem 1}
${voffset 2}${top_mem name 2}${alignr}${top_mem cpu 2}   ${top_mem mem 2}
${voffset 2}${top_mem name 3}${alignr}${top_mem cpu 3}   ${top_mem mem 3}
${voffset 2}${top_mem name 4}${alignr}${top_mem cpu 4}   ${top_mem mem 4}
${voffset 6}${color #5397d6}STORAGE ${hr 2}$color
${voffset 2}HD: ${voffset 0}${fs_free /home}/${fs_size /home} ${alignr 1}${fs_bar 6,50 /home}
${if_mounted /media/DATA}${voffset 2}SD/USB: ${voffset 0}${fs_free /media/DATA}/${fs_size /media/DATA} ${alignr}${fs_bar 6,50 /media/DATA}${endif}
${color #5397d6}NETWORK ${hr 2}$color
${voffset 2}Upload: ${alignr}${upspeedf eth2} KB/s
${voffset 2}Download: ${alignr}${downspeedf eth2} KB/s
```
and if you want to change the font click on search for and replace text
and replace Sans with your new font.

---

### Post by vickoxy on 2010-02-10
Thanks-i will try it later-then i will post result...

---

### Post by vickoxy on 2010-02-10
Ok, i tried it now-works perfect-thanks a lot, stinkeye!!!:popcorn:

---

