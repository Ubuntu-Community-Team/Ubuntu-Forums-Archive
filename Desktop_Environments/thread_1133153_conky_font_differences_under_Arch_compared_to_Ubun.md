---
title: "conky font differences under Arch compared to Ubuntu"
date: 2009-04-22
forum: Desktop Environments
---

### Post by graysky on 2009-04-22
I'm using the same basic .conkyrc when I'm booted into Arch as I do when I'm booted Ubuntu.  For some reason, the one under Ubuntu looks different font-wise.  In the screenshot below, Arch has the light blue background while Ubuntu has the slate colored one.  Anyone know what might be causing this?

[img]http://img87.imageshack.us/img87/8700/screenshot2q.png[/img]

Here is the first part of the ~/.conkyrc
```
background no
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

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
#own_window_transparent no
#own_window_colour hotpink
# Text alpha when using Xft
xftalpha 0.8

on_bottom yes

# Update interval in seconds
update_interval 2
# Create own window instead of using desktop (required in nautilus)
#own_window no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
#minimum_size 250 5
maximum_width 258

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
#alignment top_right
alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 12
gap_y 37
# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer no

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no
```

---

### Post by JECHO on 2009-04-22
> **graysky said:**
> I'm using the same basic .conkyrc when I'm booted into Arch as I do when I'm booted Ubuntu.  For some reason, the one under Ubuntu looks different font-wise.  In the screenshot below, Arch has the light blue background while Ubuntu has the slate colored one.  Anyone know what might be causing this?

[img]http://img87.imageshack.us/img87/8700/screenshot2q.png[/img]

Here is the first part of the ~/.conkyrc
```
background no
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

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
#own_window_transparent no
#own_window_colour hotpink
# Text alpha when using Xft
xftalpha 0.8

on_bottom yes

# Update interval in seconds
update_interval 2
# Create own window instead of using desktop (required in nautilus)
#own_window no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
#minimum_size 250 5
maximum_width 258

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
#alignment top_right
alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 12
gap_y 37
# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer no

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no
```


maybe you don't have the font you're specifying installed on both systems

---

### Post by kerry_s on 2009-04-22
it looks to me like your running different dpi, arch looks smaller maybe 96, ubuntu looks like it's about 100, there both mono you can tell by the "0".

in arch you can put> Xft.dpi: 100 <in ~/.Xdefaults
in ubuntu its in appearance.

you didn't say which look you want. :)

---

### Post by graysky on 2009-04-23
> **kerry_s said:**
> it looks to me like your running different dpi, arch looks smaller maybe 96, ubuntu looks like it's about 100, there both mono you can tell by the "0".

in arch you can put> Xft.dpi: 100 <in ~/.Xdefaults
in ubuntu its in appearance.

you didn't say which look you want. :)

I like the Ubunutu look better... when I booted into arch, I don't have an ~/.Xdefaults at all.  Should I make one and have it only contain that single line (Xft.dpi: 100)?

---

### Post by kerry_s on 2009-04-23
yes, you have to make it in any distro. it's for extra settings.
[http://wiki.archlinux.org/index.php/Xdefaults](http://wiki.archlinux.org/index.php/Xdefaults)

here's what mine looks like:

```
Xft.dpi: 100
Xft.antialias: true
Xft.hinting:  true
Xft.hintstyle:  hintfull
Xft.rgba: none 

*customization: -color
*font: 9x15
*enableBackups: off
*scrollBar: false

Xcursor*size: 36

xterm*reverseVideo: true
xterm*geometry: 100x35
xterm*cursorBlink: false

xmessage*font: 10x20
xmessage.form.message.Scroll: WhenNeeded

xcalc.ti.Command.foreground: White
xcalc.ti.Command.background: black
xcalc.ti.button5.background: Orange
xcalc.ti.button20.background: red
xcalc.ti.button25.background: red
xcalc.ti.button30.background: red
xcalc.ti.button35.background: red
xcalc.ti.button40.background: red
xcalc.ti.button22.background: navyblue
xcalc.ti.button23.background: navyblue
xcalc.ti.button24.background: navyblue
xcalc.ti.button27.background: navyblue
xcalc.ti.button28.background: navyblue
xcalc.ti.button29.background: navyblue
xcalc.ti.button32.background: navyblue
xcalc.ti.button33.background: navyblue
xcalc.ti.button34.background: navyblue
xcalc.ti.button37.background: navyblue
xcalc.ti.button38.background: blue

```

---

