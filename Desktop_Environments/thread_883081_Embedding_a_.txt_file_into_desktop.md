---
title: "Embedding a .txt file into desktop"
date: 2008-08-07
forum: Desktop Environments
---

### Post by CloudFX on 2008-08-07
I've heard that it is possible (and quite simple) to embed a .txt file into your desktop.  It seems as if this is possible to do with Conky, but I'm clueless at configurating it.  

Would anybody, by any chance, have this configuration, or know of another application that I can use to do this? 

Thanks!

---

### Post by finer recliner on 2008-08-07
it can be done with conky. i can make a config file for you tonight when i get home

---

### Post by finer recliner on 2008-08-07
the following should work for you. put the text below in a file called .conkyrc and put it in your home folder. you only need to edit the last line of this file to point at the path of the text file you want to display. the number on the last line (30) is how many seconds you want conky to wait before refreshing this part of the output. change any part of this want (colors, refresh times, location on desktop, etc). look at the man page for more information. let me know how it works out.

```

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft no

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline yes # amplifies text if yes
draw_borders no
#font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 20


# stuff after 'TEXT' will be formatted on screen

TEXT
${execi 30 cat /path/to/text/file}

```

---

### Post by Cesaar on 2010-12-07
> **finer recliner said:**
> the following should work for you. put the text below in a file called .conkyrc and put it in your home folder. you only need to edit the last line of this file to point at the path of the text file you want to display. the number on the last line (30) is how many seconds you want conky to wait before refreshing this part of the output. change any part of this want (colors, refresh times, location on desktop, etc). look at the man page for more information. let me know how it works out.

```

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft no

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline yes # amplifies text if yes
draw_borders no
#font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 20


# stuff after 'TEXT' will be formatted on screen

TEXT
${execi 30 cat /path/to/text/file}

```
Hey, I'm not the person that originally requested pointers for this configuration, but it works beautifully. This is exactly what I needed in order to embed information on my desktop like tasks and pending homework etc, without having to have a text editor open or without directly editing the background image. Thanks so much!

---

