---
title: "Conky Startup Script"
date: 2010-05-06
forum: Desktop Environments
---

### Post by AdamMPkins on 2010-05-06
I'm having trouble getting conky to boot friendly-like with the gwm. If I just set conky as a start up program, it floats above other windows, it seems to have loaded before the desktop actually did.

So I googled it and found that many people use the conky shell scripts to make it sleep until the desktop load. I created one, made it executable, and restarted to see the effect and found that conky never launched at all (not visible, no running process).

Here is my startup shell script for conky:
```
#!/bin/bash
sleep 10 && conky;

```
 This is how it should look if working properly. If I launch conky AFTER login, it looks like this every time.
[http://imgur.com/GdE9f&Uq4SS](http://imgur.com/GdE9f&Uq4SS)

This is how it looks if I simply set it to open upon startup with no script.
[http://imgur.com/GdE9f&Uq4SSl](http://imgur.com/GdE9f&Uq4SSl)

If I try to open it with the script, I simply never see anything in conkys place. It seems like the script never executes. How can I troubleshoot this? I'm not even sure what else to try. I've tried setting longer and shorter sleep times, but I never see so much as a single instance of conky running.

---

### Post by AdamMPkins on 2010-05-07
Am I doing something wrong here? I've posted a couple threads about various subjects related to conky with zero responses. Am I posting it in the wrong forum or not providing enough information?

---

### Post by Random_Dude on 2010-05-07
When you did the script, did you do it like this?

[http://ubuntuforums.org/showpost.php?p=2309149&postcount=4](http://ubuntuforums.org/showpost.php?p=2309149&postcount=4)

This one worked fine for me.

Cheers :cool:

---

### Post by AdamMPkins on 2010-05-08
The script seems to be launching conky on a delay now but it's still floating. I've tried setting the sleep times longer with no luck. Here is my conkyrc, are there any reasons in the script that might be causing conflicts?

```
background yes
use_xft yes
xftfont Candara UI:size=9:bold
xftalpha 0.5
update_interval 1.0
total_run_times 0
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 300 5
maximum_width 300
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color black
default_shade_color red
default_outline_color green
alignment top_right
gap_x 12
gap_y 50
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no
color1 ffffff # white
color2 ff0000 # red

TEXT
${color1}

${time %A}$alignr${time %F}

Uptime $alignr $uptime

CPU0: ${freq}MHz   $cpu%  $cpubar
CPU1: ${freq}MHz   $cpu%  $cpubar

RAM ($memmax):  $memperc%   ${membar 6}
Swap ($swapmax): $swapperc%   ${swapbar 6}

${addr eth1}

Download $alignr ${downspeed eth1} kb/s
${downspeedgraph eth1}
Upload   $alignr ${upspeed eth1} kb/s
${upspeedgraph eth1}

Reddit

${if_empty ${rss http://www.reddit.com/message/unread/.rss?feed=4fe2dec9dc3dac36b5e0b97eef3e9e8ce474ef73&user=Probablynotclever 1 item_titles 1}}${image ~/.conky/nomail.png -p 52,337}${else}${image ~/.conky/mail.png -p 52,337}${endif}

Gmail  ${color2} ${execi 60 perl ~/scripts/gmail.pl n} ${color} ${color1} unread messages


```

---

### Post by Random_Dude on 2010-05-08
See if this thread helps.
[http://ubuntuforums.org/showthread.php?t=1126007&highlight=conky+border](http://ubuntuforums.org/showthread.php?t=1126007&highlight=conky+border)

Cheers :cool:

---

### Post by AdamMPkins on 2010-05-09
> **Random_Dude said:**
> See if this thread helps.
[http://ubuntuforums.org/showthread.php?t=1126007&highlight=conky+border](http://ubuntuforums.org/showthread.php?t=1126007&highlight=conky+border)

Cheers :cool:

This fixed it. thanks a lot!

---

### Post by Random_Dude on 2010-05-09
You're welcome, glad I helped.
Thank  stinkeye and johnc4510, those hits are really good.


Hit the [SOLVED] option. :cool:

---

### Post by AdamMPkins on 2010-08-31
I'd like to hit solved. I've looked up and down the thread though and cant find the option.

---

### Post by AdamMPkins on 2010-08-31
Found it.

---

