---
title: "[CONKY] check eth0 or wlan0"
date: 2008-02-21
forum: Desktop Effects &amp; Customization
---

### Post by Choxo on 2008-02-21
Hi,

I would like to see on my desktop my ip. 
The problem is that I often switch betwenn wired&wireless.
Is there a way in conky to check if I'm connected wired or wireless?

I know if_running exists, but is there something like if_wirless and if_wired ?

Thanks !

---

### Post by applehead on 2008-02-21
How about this browser extension
[https://addons.mozilla.org/en-US/firefox/addon/590]("https://addons.mozilla.org/en-US/firefox/addon/590")

---

### Post by Choxo on 2008-02-21
Sorry but how can a Firefox plugin help me with a conky script?

---

### Post by PurposeOfReason on 2008-02-21
> **Choxo said:**
> Sorry but how can a Firefox plugin help me with a conky script?
Here is my one of my conkyrc's. If you read it, you'll get it.
```
 #avoid flicker
double_buffer yes

#own window to run simultanious 2 or more conkys
own_window  yes
own_window_transparent yes
own_window_type override
own_window_hints undecorate,sticky,skip_taskbar,skip_pager 

background true

#borders
draw_borders no
border_margin 3

#shades
draw_shades no

#position
gap_x 5
gap_y 5
alignment top_right

#behaviour
update_interval 3

#color
default_color  000000
color1 d1d1d1
color2 d1d1d1

#font
use_xft yes
xftfont Myriad Pro:pixelsize=14

#to prevent window from moving
use_spacer yes

#mpd
mpd_host localhost
mpd_port 6600

minimum_size 180 5
maximum_width 180 30

TEXT
${alignr}${if_existing /sys/class/net/wlan0/operstate up}${alignr}//${color1}Arch-Updates ${color}  //${color1}${texeci 10800 perl /home/shawn/.scripts/conky-updates.pl}${color}${else}${if_existing /sys/class/net/eth0/operstate up}${alignr}//${color1}Arch-Updates ${color}  //${color1}${texeci 10800 perl /home/shawn/.scripts/conky-updates.pl}${color}${else}${endif}${endif}
```

---

### Post by waldorsockbat on 2008-02-21
you could add this to your .conkyrc for wireless

${color slate grey}IP Address:    ${color }${addr ath0}
${color slate grey}SSID   ${color }${wireless_essid ath0} ${alignr}${wireless_link_qual_perc ath0}
${color slate grey}Mode ${color }${wireless_mode ath0} ${alignr}${color slate grey}Bitrate:${color } ${wireless_bitrate ath0}
${color slate grey}Down:  ${color white}${downspeed ath0}Kb/s ${alignr}${color slate grey}Up:  ${color white}${upspeed ath0}
${color slate grey}Down:  ${color white}${totaldown 
ath0}${alignr}${color slate grey}Up: ${color white}${totalup ath0}  

and then this under it for your wired connection. just change ath0 to eth0 or eth1 which ever you interface is.you can edit this to make it look like you want in conky. hope this helped.

${color slate grey}IP Address:    ${color }${addr ath0}
${color slate grey}Mode ${color }${wireless_mode ath0} ${alignr}${color slate grey}Bitrate:${color } ${wireless_bitrate ath0}
${color slate grey}Down:  ${color white}${downspeed ath0}Kb/s ${alignr}${color slate grey}Up:  ${color white}${upspeed ath0}
${color slate grey}Down:  ${color white}${totaldown 
ath0}${alignr}${color slate grey}Up: ${color white}${totalup ath0}

---

### Post by applehead on 2008-02-21
> **Choxo said:**
> Sorry but how can a Firefox plugin help me with a conky script?

you're welcome.

---

### Post by PurposeOfReason on 2008-02-21
> **applehead said:**
> you're welcome.
For what? I just quoted him, that script has nothing to do with firefox.

---

### Post by Choxo on 2008-02-22
Thanks man!

It's working now!

---

