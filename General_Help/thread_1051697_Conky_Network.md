---
title: "Conky Network"
date: 2009-01-27
forum: General Help
---

### Post by Bofur on 2009-01-27
I have a problem with my conky - its not detecting my network SSID. For "Network" is just says unk%. I have it set as eth1, which is my wireless. The download and upload work just fine. Don't really understand whats wrong. Heres the output:
```
background no
double_buffer yes
use_xft yes

default_color EFEFEF
default_shade_color black
default_outline_color white
own_window_colour 262729

#own window to run simultanious 2 or more conkys

own_window  yes

own_window_transparent yes

own_window_type normal

own_window_hints undecorate,sticky,skip_taskbar,skip_pager 



#borders

draw_borders no

border_margin 0



#shades

draw_shades yes



#position

gap_x 0

gap_y 0

alignment bottom_middle



#behaviour

update_interval 3


#font

use_xft yes

xftfont Droid:pixelsize=12


#to prevent window from moving

use_spacer none

minimum_size 1200
maximum_width 1920


TEXT
${voffset 1}  Kern: $kernel | ${color white}${time %I:%M %p}$color ${time %A, %d %b  %y}  |  ${color} Up: ${color white}${uptime_short}  |  ${color white}${acpitemp}°C  |  ${color}Cpu: ${color white}${cpu cpu0}%  ${color}${cpugraph 8,24 AEA08E 9F907D cpu0} ${color white} ${color white}${cpu cpu1}%  ${color}${cpugraph 8,24 AEA08E 9F907D cpu1} ${color white}  |  ${color }Mem: ${color white} $memperc% ${membar 6,36}${color }  |   Home: ${fs_used_perc /home}% ${fs_bar 6,36 /home} ${fs_free /home} left |  ${color}Net: ${color white}${wireless_essid eth1} ${wireless_link_qual_perc eth1}%  ${color}Down: ${color white}${font}${downspeed eth1} Kb/s ${color} - ${color}Up: ${color white}${font}${upspeed eth1} Kb/s  |  Bat : ${battery_bar 6,24 BAT0}
```

---

### Post by cdtech on 2009-01-27
What's the output of "iwconfig"? I had to use a small script to pull my ESSID from iwconfig:
```
iwconfig wlan0 | sed 's/  /\n/g' | grep ESSID | sed 's/ESSID:"//'| sed 's/"//'
```

---

### Post by Bofur on 2009-01-27
```
justin@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
pan0      no wireless extensions.

justin@ubuntu:~$ 


```

---

### Post by Bofur on 2009-01-27
Bump

---

### Post by detroit/zero on 2009-01-28
From that output, it doesn't look like you have an essid for any device. There's a lot of info missing from that. Here's mine, for example:```
zero@zero-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"XXXXXXXXXX"  Nickname:""
          Mode:Managed  Frequency:2.417 GHz  Access Point: XX:XX:XX:XX:XX
          Bit Rate:54 Mb/s   Tx-Power:17 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=60/70  Signal level=-34 dBm  Noise level=-94 dBm
          Rx invalid nwid:5974  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by swoody on 2009-02-09
Bump for us both. I have the same exact problem as Bofur - my essid and signal strength don't work in conky, but my up/down speeds do. The output of 'iwconfig' is the same as his as well:

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
pan0      no wireless extensions.


```

---

### Post by ngaro on 2010-11-10
For people still looking for the problem, I just answered this in the conky bugtracker at [https://sourceforge.net/tracker/?func=detail&aid=3104701&group_id=143975&atid=757308](https://sourceforge.net/tracker/?func=detail&aid=3104701&group_id=143975&atid=757308) .
Your problem lies not with conky but a layer lower.

---

