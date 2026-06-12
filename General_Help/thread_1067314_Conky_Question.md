---
title: "Conky Question"
date: 2009-02-11
forum: General Help
---

### Post by WildeBeest on 2009-02-11
Can the conky script be displayed on all 4 desktops?

If so, how?

---

### Post by mtbsoft on 2009-02-11
You need to set... 

```
own_window yes
```

...and... 

```
own_window_hints sticky
```

...in the conky file at least.  This will make it create and use its own window instead of the desktop and then sticks the window to all desktops.  There are other own_window_hints settings but this would be the absolute minimum.

---

### Post by WildeBeest on 2009-02-12
Thanks for the reply.

It didn't work for me.

This is what I have: 

```
background yes
cpu_avg_samples 2
net_avg_samples 2
out_to_console no
text_buffer_size 2048
max_user_text 16384
max_specials 5120
use_xft yes
xftfont monospace-9
own_window_transparent yes
own_window_colour hotpink
xftalpha 0.8
mail_spool $MAIL
update_interval 1
own_window yes
own_window_hints sticky
own_window_type override
double_buffer yes
minimum_size 120 5
maximum_width 270
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
stippled_borders 0
border_margin 10
border_width 1
default_color white
default_shade_color white
default_outline_color white
alignment top_right
gap_x 5
gap_y 20
use_spacer left
no_buffers yes
uppercase no

TEXT

```

---

### Post by Netsu on 2009-02-12
```
double_buffer yes
#!/bin/sh
sleep 1 && feh --bg-center ~/background.png &
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```
Thats what works for me, dont understand half of it though, got it from some other forums.

---

### Post by WildeBeest on 2009-02-12
I'll give it a shot.

---

### Post by WildeBeest on 2009-02-14
Didn't work.

I don't get conky to display on any desktop.

---

### Post by WildeBeest on 2009-03-25
Bump for an answer.

Conky does diplay on Desktop 1, How do I get it on the rest?

---

