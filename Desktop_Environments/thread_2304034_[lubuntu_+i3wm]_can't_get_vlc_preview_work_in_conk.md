---
title: "[lubuntu +i3wm] can't get vlc preview work in conkybar"
date: 2015-11-23
forum: Desktop Environments
---

### Post by Niklas_Wnsche on 2015-11-23
hello everybody. I'm using lubuntu 15.04 with i3wm and I really like it. I wanted to customize my statusbar with conky and everything worked, except the vlc--preview. I dont know why, it looks like the scripts deletes a bracket, but I don't know why. It would so cool if somebody of you could help me. Greetings, Niklas

  .conkyrc:  

```

out_to_x no
own_window no
out_to_console yes
background no
max_text_width 0
update_interval 1.0
total_run_times 0
short_units on
if_up_strictness address
use_spacer right
override_utf8_locale no
cpu_avg_samples 1

TEXT
[
{ "full_text" : " RAM ${mem}/${memmax} " , "color" : ${if_match ${memperc}<90}"\#ffffff"${else}"\#ff0000"${endif} },
{ "full_text" : " ${if_up wlan0}WLAN &#8593;${upspeed wlan0} &#8595;${downspeed wlan0}  ${endif}\
"},
{ "full_text" : " Akku: ${battery_percent}% " , "color" : ${if_match ${battery_percent}<=20}"\#ff0000"${else}"\#ffffff"${endif}\
},
{ "full_text" : ${if_running vlc}VLC: ${exec ./vlc22.sh}${endif}\
"},
{ "full_text" : "${if_running spotify} ${exec ~/6800547/spotify.sh metadata | grep  "artist" | cut -d '|' -f2} - ${exec ~/6800547/spotify.sh metadata | grep  "title" | cut -d '|' -f2} | ${endif}\
${time %a %d.%m.%y} ${time %H:%M} " }

],

```

vlc22.sh:

```

#!/bin/bash
nc -U /tmp/vlc.sock <<< "get_title"

```

conky:

```

fox@fox-ThinkPad-L450:~$ conky
[
{ "full_text" : " RAM 924MiB /7.52GiB " , "color" : "#ffffff" },
{ "full_text" : " WLAN &#8593;0B      &#8595;0B       "},
{ "full_text" : " Akku: 83% " , "color" : "#ffffff"},
"},full_text" : VLC: Sunburn
{ "full_text" : "Mo 23.11.15 23:08 " }
],

```

---

### Post by SlidingHorn on 2015-11-23
Just to be sure: Your vlc22.sh is in the same directory as your .conkyrc?

---

### Post by Niklas_Wnsche on 2015-11-24
Yes, it is.

---

