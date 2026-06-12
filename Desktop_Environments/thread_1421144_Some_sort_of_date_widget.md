---
title: "Some sort of date widget?"
date: 2010-03-03
forum: Desktop Environments
---

### Post by ferret man on 2010-03-03
I am trying to free up space on my desktop and I would like to know if there is something that (without a panel) can tell the date from the desktop... some sort of widget perhaps, or maybe something even sort of in the wallpaper. I need extra space on my desktop because I only have a 9 inch screen. Thank you for your time.

---

### Post by mcduck on 2010-03-04
Sure there are, actually many different options so you can just pick what you like best.

The most lightweight option would probably be Conky, and if you select a nice font it will most likely also be the best looking one so that's what I'd use. But it's configured by editing a text file by hand which isn't for everybody... (Conky is able to print all kind of info in text format into your desktop, you'll find sevral threads in this forum where people are sharing their configurations and posting screenshots)

The second best looking, and a lot easier, option is to install Screenlets, I'm sure it has at least one widget that does what you want. If you don't thik Conky is for you then I suggest trying this one. (screenlets is more typical desktop widget applicaatn, with a large selection of different widgets available)

Then there are plenty of other apps tha you can use to add information to your desktop, gDesklets, aDesklets, Gkrellm and countless others...

---

### Post by BenAshton24 on 2010-03-04
+1 for conky

---

### Post by ferret man on 2010-03-04
I installed Conky, but I am not sure how to configure it.. I would like it in the middle of my screen displaying the time and date if that is possible. Can someone please help me configure this.

---

### Post by wojox on 2010-03-04
Probably need something like this saved as .conkyrc in your Home Folder:

```

background yes
use_xft yes
xftfont 123:size=8
xftalpha 0.1
update_interval 0.5
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 250 5
maximum_width 400
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color gray
default_shade_color red
default_outline_color green
alignment top_center
gap_x 10
gap_y 10
no_buffers no
uppercase no
override_utf8_locale yes
use_spacer yes
text_buffer_size 256

TEXT

${color DarkSlateGray} ${font :size=30}$alignc${time %H:%Mh}
${voffset -30}${font :bold:size=10}$alignc${time %d %b. %Y}
${font :bold:size=8}$alignc${time %A}

```

---

### Post by ferret man on 2010-03-04
That was perfect, thank you so much!

---

