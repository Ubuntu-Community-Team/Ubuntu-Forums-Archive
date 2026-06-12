---
title: "How to  - custom conky theme with fortune quotes. Ubuntu 16.04"
date: 2016-05-02
forum: Desktop Environments
---

### Post by dadoprom-3 on 2016-05-02
[ATTACH=CONFIG]268797[/ATTACH]

I wanted to have random quotes on my desktop. I searched for a while and I have put together pieces and bits of codes. And, what you see on the screenshot of my desktop is the result. If anybody would like to achieve the same result, follow this guide.

1. install conky and fortune: sudo apt-get install conky fortune
2. From your home drive, create a file in your text editor called .conkyrc 
3. Open .conkyrc with your text editor (gedit)
4. Copy and paste my configuration - theme (I didn't create it, it is someone’s other work, credits go there :). I just made some small adjustments)

```

use_xft yes
xftfont 123:size=8
xftalpha 0.1
update_interval 1
total_run_times 0

own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_colour 000000
own_window_argb_visual yes
own_window_argb_value 0

double_buffer yes
#minimum_size 250 5
#maximum_width 500
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color white
default_shade_color red
default_outline_color green
alignment middle_right
gap_x 110
gap_y 10
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 1
override_utf8_locale yes
use_spacer yes

minimum_size 120 520
TEXT
${voffset 10}${color EAEAEA}${font GE Inspira:pixelsize=120}${time %H:%M}${font}${voffset -84}${offset 10}${color 1793D1}${font GE Inspira:pixelsize=42}${time %d} ${voffset -15}${color EAEAEA}${font GE Inspira:pixelsize=22}${time %B} ${time %Y}${font}${voffset 24}${font GE Inspira:pixelsize=58}${offset -148}${time %A}${font}

${voffset -1}
${font Ubuntu:pixelsize=20}${offset 0}${execi 300 fortune | fold -w96}

```

5. Save changes, save file.
6. Hit Alt+F2, write "conky", hit enter

Now everything should be up and running. Except you may not like the default quotes which come with fortune. If you wish to make your own quotes file, follow these steps>

HOWTO: create custom fortune cookies files (credits> [http://ubuntuforums.org/showthread.php?t=1343692](http://ubuntuforums.org/showthread.php?t=1343692))
Open your favourite editor and add the strings that you want to be shown when running "fortune" in terminal. BE SURE to add a single line with a letter % in it, between every string. Save this file to whatever file name you want; this guide uses "yourlist" as example. When done adding strings, run the command "strfile -c % yourlist yourlist.dat". This will create a .dat file for your cookie file, which contains a header structure and a table of file offsets for each group of lines. This allows random access of the strings. Run "fortune yourlist" to eat the fruit of your work. That's it! If you want this cookie file to appear as any other of the standard fortune cookies (when simply running "fortune"), just add your string file and .dat file into "/usr/share/games/fortunes/". Oh, and one more thing: if you want to change anything in "yourfile", you will need to repeat this HOWTO again for it to work.

I deleted all the quotes in "/usr/share/games/fortunes/" and used only my file.
Good luck!

---

### Post by Yashalta on 2016-10-13
Thanks!

---

