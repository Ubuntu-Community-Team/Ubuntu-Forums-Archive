---
title: "My Conky - again - not set properly..."
date: 2010-02-22
forum: Desktop Environments
---

### Post by vickoxy on 2010-02-22
Hi,
i just reinstalled my xubuntu (for the third time) and still again i have major problem with my conky. I copied all conky files from previous xubuntu (same version as now-9.10), but no way i can have the same appearance as before-the font is too big, an everything seems to ugly.

I am missing something?

```
# Use Xft?
use_xft yes
xftfont Andale Mono:size=7
xftalpha 0.8
text_buffer_size 2048

# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_type override
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 160 0
maximum_width 170 0

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 5

# border width
border_width 1

# Default colors and also border colors
default_color white
#default_shade_color black
#default_outline_color white
own_window_colour white

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 3
gap_y 23

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
use_spacer none

# Network Options
if_up_strictness address

TEXT
${font Arial:size=26}${alignc}${time %H:%M:%S}${font}
${alignc}${time %A, %d.%m.%Y}
${hr 2}
${execpi 300 cal | sed -e 's/'`date | awk '{print $3}'`'/\$\{color e84448}'`date | awk '{print $3}'`'\$\{color}/'|sed 's/^/${alignc}/'}
${voffset -20}SYSTEM ${hr 2}
${cpugraph 000000 ffffff}
${voffset 2}CPU: ${cpu}% ${alignr 1} ${alignr}${freq}MHz   ${acpitemp}C
${voffset 2}HDD Temp${alignr}${hddtemp /dev/sda localhost 7634}C
${voffset 2}RAM: $memperc% ${alignc} $mem${alignr 7} ${membar 6,50}
${voffset 2}HD: ${voffset 0}${fs_free /home}/${fs_size /home} ${alignr 1}${fs_bar 6,50 /home}
${if_mounted /media/DATA}${voffset 2}SD/USB: ${voffset 0}${fs_free /media/DATA}/${fs_size /media/DATA} ${alignr}${fs_bar 6,50 /media/DATA}${endif}
NETWORK ${hr 2}
${voffset 2}Upload: ${alignr}${upspeedf eth2} KB/s
${voffset 2}Download: ${alignr}${downspeedf eth2} KB/s
${voffset 6}MAIL ${hr 2}
```

---

### Post by koleoptero on 2010-02-22
At first I'd like to point out that it's better if you change the own_window_type to override.

Secondly, the conky seems to be using the font Arial, so you need to install the ttf-mscorefonts-installer package to install the microsoft fonts by typing in a terminal:

sudo aptitude install ttf-mscorefonts-installer

Then wait a minute and restart conky, and tell me if it worked. :)

---

### Post by vickoxy on 2010-02-22
> **koleoptero said:**
> At first I'd like to point out that it's better if you change the own_window_type to override.

Secondly, the conky seems to be using the font Arial, so you need to install the ttf-mscorefonts-installer package to install the microsoft fonts by typing in a terminal:

sudo aptitude install ttf-mscorefonts-installer

Then wait a minute and restart conky, and tell me if it worked. :)

The first thing i did was to install **ttf-mscorefonts-installer** but it seems as it not recognize that normal mono any more.

Same conky-see here the fonts:
[http://ubuntuforums.org/showthread.php?t=1411313](http://ubuntuforums.org/showthread.php?t=1411313)

---

### Post by vickoxy on 2010-02-22
I updated conkyrc and the picture-still the font i am having there is more stretched as the old one-the same conkyrc...  if i use size 6 it is barely readable.

---

### Post by koleoptero on 2010-02-22
That struck me as weird cause I don't remember ever seeing a font named just "mono". If that's the problem try the monospace or the courier 10 pitch fonts, or any other monospace font for that matter. But I have the microsoft fonts installed too and there's no just "mono" named font installed. Perhaps you had it installed from some other source?

---

### Post by vickoxy on 2010-02-22
No-but my last xubuntu installation was very weird-i had probably bad usb stick, and lots of things are working now totally different as before. Still, i miss that font that i had-i used now fonts you suggested, but they are still not so pleasant to look as the old one... (i even set the size to 6, but it&#347; too small

---

### Post by koleoptero on 2010-02-22
You can also try the Terminus font from here: [http://fractal.csie.org/~eric/wiki/Terminus_font](http://fractal.csie.org/~eric/wiki/Terminus_font)
It's considered to be one of the best monospace fonts. :)

EDIT: Now that I looked at those pictures again it also looks like the font smoothing was different in the older one too. But I still believe it's because of the missing font.

EDIT 2: Also for whatever conky related needs you have, you should ask in this thread: [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)
The guys there are very helpful and really know their way around conky configs. :)

---

### Post by vickoxy on 2010-02-23
> **koleoptero said:**
> You can also try the Terminus font from here: [http://fractal.csie.org/~eric/wiki/Terminus_font](http://fractal.csie.org/~eric/wiki/Terminus_font)
It's considered to be one of the best monospace fonts. :)

EDIT: Now that I looked at those pictures again it also looks like the font smoothing was different in the older one too. But I still believe it's because of the missing font.

EDIT 2: Also for whatever conky related needs you have, you should ask in this thread: [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)
The guys there are very helpful and really know their way around conky configs. :)

Well i just found few mono fonts that are looking the way i think they should, and now everything is ok.
tahnks koleoptero:popcorn:

---

### Post by Sector11 on 2010-02-24
> **vickoxy said:**
> Hi,
i just reinstalled my xubuntu (for the third time) and still again i have major problem with my conky. I copied all conky files from previous xubuntu (same version as now-9.10), but no way i can have the same appearance as before-the font is too big, an everything seems to ugly.

I am missing something?

```
# Use Xft?
use_xft yes
xftfont Andale Mono:size=7
xftalpha 0.8
text_buffer_size 2048

```

Yes, probably the font: "Andale Mono" that conky wants to use!

---

