---
title: "make conky automatically resize"
date: 2010-04-26
forum: Desktop Environments
---

### Post by marranzano on 2010-04-26
hello,
I have a conky setup for displaying mpd.
this is the code:
```
# Use Xft?
imlib_cache_size 0          # so image is redrawn
use_xft yes 
xftalpha 0
text_buffer_size 2048
font Arial:size=9

border_inner_margin=50
pad_percents=50

# Update interval in seconds
update_interval 2

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,skip_taskbar

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
#minimum_size 450
#maximum_width 1000

# Draw shades?
draw_shades no

# Default colors and also border colors
default_color white

# Text alignment, other possible values are commented
alignment bottom_left

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 10
gap_y 10

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer right
alignment                   bl

TEXT
${font 911 Porscha:size=12}${color 222222}MPD${font :size=8}${tab 45}Rnd ${mpd_random} / Rpt ${mpd_repeat}${font :size=9:style=bold}${tab 150}${mpd_status}${color 888888}
${execi 2 ~/.conky/cover.sh}
${image /tmp/mpdcover.jpg -s 80x80 -p 3,23}${tab 90}${voffset -8}${font :size=14:style=Bold}${mpd_artist}  
${tab 105}${voffset 2}${font :size=12:style=Bold}${mpd_title}  
${tab 90}${voffset 4}${font :size=8:style=bold}${mpd_track}  ${voffset -2}${font :size=10}${mpd_album}  
${tab 5}${voffset 15}${font :size=9:style=bold}${color 222222}${mpd_elapsed} / ${mpd_length}${tab 15}${mpd_bar 6,260}
```

everything works well but i would like it to resize when the song has a long title instead of cutting it...

how do i tell it to resize?
thanks

---

### Post by snkiz on 2010-04-26
These two lines:
```

# Minimum size of text area
#minimum_size 450
#maximum_width 1000

```

uncomment them and ajust to your needs.

---

### Post by marranzano on 2010-04-27
> **snkiz said:**
> These two lines:
```

# Minimum size of text area
#minimum_size 450
#maximum_width 1000

```

uncomment them and ajust to your needs.

I've been experimenting with those two lines but the result is that the width of conky will depend on the length of title of the first song played, no matter the length of the titles of the following songs.

Therefore it doesn't automatically adjust with new songs... :confused:

---

### Post by marranzano on 2010-05-08
the problem is in the
${tab}
option:
when the window resizes due to a new song title the new window size doesn't include the tab...

if the title is x in length the window will be x in length no matter the tab in front of the title, resulting in having the window cut the title...:

___tab__________title________   
|_______|__________________|

______window=title___
|__________________|


the whole point of my config is to have the album's cover before the title (inside the tab)...

so far no solution, if not to change the layout ](*,)

---

### Post by SpeedyGonsales on 2012-06-26
Same problem here, not mpd but it seems conky<=1.8.1 resizes window only on restart, not on every ```
update_interval
``` parameter.

This is on conky bug tracker as bug & feature request from 2009, seems won't be fixed.

Conky 1.9.0 resizes fine, if your lines are truncated, try setting

```
text_buffer_size
```

to something more than default 256. For me 1000 is enough, 400 was not.

---

### Post by oldos2er on 2012-06-26
Old thread closed; please don't bump old threads.

---

