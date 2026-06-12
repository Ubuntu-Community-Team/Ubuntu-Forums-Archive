---
title: "Ultra_Man needs conky help"
date: 2009-12-28
forum: Desktop Environments
---

### Post by Ultra_Man on 2009-12-28
^Title is like that so I can find it easier.

1.)How can I move, for example, the stuff on the top left nearer to the gunbarrel?

Image here: [http://i.neoseeker.com/mgv/350752-Bass%20Ultra/752/11/december_28_09.png](http://i.neoseeker.com/mgv/350752-Bass%20Ultra/752/11/december_28_09.png)
2.)Also, how do I get rid of the extra stuff like, Hardy root, hardy-home, mac, cause I just got this config from somewhere. :)
```
# -*- conf -*-
#
# ~/.conkyrc - Conky configuration file
#
# By arpbook http://www.arpbook.com
#
# Heavily inspired by .conkyrc file of
# Henrik Brix Andersen <henrik@brixandersen.dk>
#
# Thanks to him.
#
#
# ·ë{¶«¡Çø}—æÂê®Úîœô€âÒÌÏÈ¬µÙ@©&#9830;ß~÷Ÿ´É[å»ÛÁ]–ÆÅÊ¤ŸªïŒÔ¥À·ÎÍË|Óû#¢~¿¿·\± 
#######################################################################
# variables ###########################################################

# fork to background ? ################################################
background no

# font settings #######################################################
use_xft yes
#font monospace-8
xftfont Acknowledge TT BRK:size=8
#xftfont Edit Undo BRK:size=8
#xftfont Visitor TT2 BRK:size=10
uppercase yes
override_utf8_local yes

# update every 1 secs #################################################
update_interval 1

# stay running forever ################################################
total_run_times 0

# draw to root window #################################################
own_window no

# avoid flickering ####################################################
double_buffer yes

# size ################################################################
minimum_size 1270 800
maximum_width 1270

# position ############################################################
alignment top_left
#alignment top_middle
#alignment top_right
#alignment bottom_left
#alignment bottom_middle
#alignment bottom_right
#alignment middle_left
#alignment middle_right
gap_x 0
gap_y 0

# colors ##############################################################
default_color white
default_shade_color white
default_outline_color black
# custom colors #######################################################
color0 FFFFFF
color1 F5F5F5
color2 A2AEC6
color3 696969
color4 D3D3D3
color5 6495ED
color6 87CEFA
color7 5F9EA0
color8 BBBBBB
color9 262729


# borders #############################################################
draw_borders no
draw_graph_borders no
stippled_borders 8
border_margin 4
border_width 1

# shades ##############################################################
draw_shades no

# outline #############################################################
draw_outline no

# spacer ##############################################################
use_spacer no

# buffers (Substract (file system) buffers from used memory?)##########
no_buffers yes

# sampling ############################################################
cpu_avg_samples 2
net_avg_samples 2

# configuration #######################################################
TEXT
${voffset 10}${offset 10}$color8 /$color3 System$color8 /
${offset 10}$color2 $sysname$color9 -$color2 $machine
${offset 10}$color2 $kernel
${offset 10}$color2 CrunchBang$color9 on$color2 $nodename
${offset 10}$color6 ${time %A %d/%m/%y %kh%M}
${offset 10}$color2 Uptime :$color6 $uptime

${offset 10}$color8 /$color3 Mails$color8 /
${offset 15}$color2 arpbook : $color4${imap_unseen mail.mac.com "adresse mac" "mot de passe mac"}
${offset 15}$color2 larnel  : $color4${imap_unseen mail.mac.com "adresse mac" "mot de passe mac"}

${voffset -100}${offset 980}$color8 /$color3 Ubuntu Planet RSS$color8 /
${offset 985}$color2 >$color4${rss http://planet.ubuntu-fr.org/feed/tag/Accueil/rss2 60 item_title 0}
${offset 990}$color2 >$color4${rss http://planet.ubuntu-fr.org/feed/tag/Accueil/rss2 60 item_title 1}
${offset 1000}$color2 >$color4${rss http://planet.ubuntu-fr.org/feed/tag/Accueil/rss2 60 item_title 2}
${offset 1005}$color2 >$color4${rss http://planet.ubuntu-fr.org/feed/tag/Accueil/rss2 60 item_title 3}
${offset 1010}$color2 >$color4${rss http://planet.ubuntu-fr.org/feed/tag/Accueil/rss2 60 item_title 4}



${offset 1040}$color8 /$color3 DYP RSS$color8 /
${offset 1045}$color2 >$color4${rss http://yaen.pujol.free.fr/dotclear/rss 60 item_title 0}
${offset 1045}$color2 >$color4${rss http://yaen.pujol.free.fr/dotclear/rss 60 item_title 1}
${offset 1045}$color2 >$color4${rss http://yaen.pujol.free.fr/dotclear/rss 60 item_title 2}
${offset 1045}$color2 >$color4${rss http://yaen.pujol.free.fr/dotclear/rss 60 item_title 3}
${offset 1045}$color2 >$color4${rss http://yaen.pujol.free.fr/dotclear/rss 60 item_title 4}

${voffset -25}${offset 70}$color8 /$color3 CPU #01$color8 /
${offset 80}$color2 Temperature :$color4 ${execi 10 sensors | grep -A 2 '^coretemp-isa-0000' | cut -c15-18 | grep '°'}C  -  $color2 Frequency : $color4${freq_dyn cpu1}$color2 MHz
${offset 80}$color2 Load: $color9 ${cpubar cpu1 6,220} $color4${cpu cpu1}$color2 %
${offset 80}$color4 ${cpugraph cpu1 15,255 262729 87CEFA}
${offset 70}$color8 /$color3 CPU #02$color8 /
${offset 80}$color2 Temperature :$color4 ${execi 10 sensors | grep -A 2 '^coretemp-isa-0001' | cut -c15-18 | grep '°'}C  -  $color2 Frequency : $color4${freq_dyn cpu2}$color2 MHz 
${offset 80}$color2 Load: $color9 ${cpubar cpu2 6,220} $color4${cpu cpu2}$color2 %
${offset 80}$color4 ${cpugraph cpu2 15,255 262729 87CEFA}

${voffset -80}${offset 1040}$color8 /$color3 CrunchBang RSS$color8 /
${offset 1045}$color2 >$color4${rss http://crunchbang.org/feed/ 60 item_title 0}
${offset 1045}$color2 >$color4${rss http://crunchbang.org/feed/ 60 item_title 1}
${offset 1045}$color2 >$color4${rss http://crunchbang.org/feed/ 60 item_title 2}

${voffset 70}${offset 20}$color8 /$color3 Wifi (ath0)$color8 /
${offset 35}$color2 essid : $color4${wireless_essid ath0}$color2 - MAC : $color4${wireless_ap ath0}
${offset 35}$color2 Wifi Level : $color4${wireless_link_qual ath0}$color2 /$color4 ${wireless_link_qual_max ath0}$color2 - Quality: $color4 ${wireless_link_qual_perc ath0}
${offset 35}$color2 IPv4 : $color4${addr ath0}$color2 -$color4 ${execi 1800 ~/.conky/ip.sh}
${offset 30}$color2 Down : $color4 ${downspeed ath0}$color2 kb/s
${offset 30}$color4 ${downspeedgraph ath0 15,250 262729 87CEFA}
${offset 30}$color2 Up : ${offset 6} $color4 ${upspeed ath0}$color2 kb/s
${offset 30}$color4 ${upspeedgraph ath0 15,250 262729 87CEFA}

${voffset -45}${offset 1060}$color8 /$color3 Power$color8 /
${offset 1055}$color2 $acpiacadapter$color4  $battery
${offset 1050}$color2 Time Left :$color4  $battery_time
${offset 1045}$color9 ${battery_bar 6,160}

${voffset 80}${offset 20}$color8 /$color3 Volumes$color8 /
${offset 35}$color2 #!-root :  $color4 ${fs_used_perc /}% - ${fs_used /} + ${fs_free /} = ${fs_size /}
${offset 35}$color9 ${fs_bar 6,320 /}
${offset 50}$color2 #!-home :  $color4 ${fs_used_perc /home}% - ${fs_used /home} + ${fs_free /home} = ${fs_size /home}
${offset 50}$color9 ${fs_bar 6,320 /home}
${offset 65}$color2 hardy-root : $color4 ${fs_used_perc /media/hardy-system}% - ${fs_used /media/hardy-system} + ${fs_free /media/hardy-system} = ${fs_size /media/hardy-system}
${offset 65}$color9 ${fs_bar 6,320 /media/hardy-system}
${offset 80}$color2 hardy-home : $color4 ${fs_used_perc /media/hardy-home}% - ${fs_used /media/hardy-home} + ${fs_free /media/hardy-home} = ${fs_size /media/hardy-home}
${offset 80}$color9 ${fs_bar 6,320 /media/hardy-home}
${offset 95}$color2 mac :   $color4 ${fs_used_perc /media/macbook-hd}% - ${fs_used /media/macbook-hd} + ${fs_free /media/macbook-hd} = ${fs_size /media/macbook-hd}
${offset 95}$color9 ${fs_bar 6,320 /media/macbook-hd}

${voffset -90}${offset 600}$color8 /$color3 Memory$color8 /
${offset 605}$color2 RAM: ${offset 0} $color9 ${membar 6,200}$color4 $mem ($memperc%)
${offset 610}$color2 Swap: $color9 ${swapbar 6,200}$color4 $swap ($swapperc%)

${voffset -90}${offset 1110}$color8 /$color3 Activity$color8 /
${offset 1105}$color2 Hdd Temp:$color4 ${hddtemp /dev/sda}
${offset 1100}$color2 Read/Write: $color4 $diskio
${offset 1090}$color2 Process :$color4 $running_processes$color2 /$color4 $processes
${offset 1090}$color6 ${top name 1}$alignr$color4 ${top cpu 1}%
${offset 1090}$color5 ${top name 2}$alignr$color4 ${top cpu 2}%
${offset 1090}$color5 ${top name 3}$alignr$color4 ${top cpu 3}%
${offset 1090}$color5 ${top name 4}$alignr$color4 ${top cpu 4}%
${offset 1090}$color5 ${top name 5}$alignr$color4 ${top cpu 5}%
${offset 1090} ${diskiograph 15,180 262729 87CEFA}
```

Random 1.)The pidgin icon doesn't show up on my tint2 sys tray? I'm using the default config by the way.

Thank you

---

### Post by stinkeye on 2009-12-29
Change these values```
TEXT
${voffset 10}[COLOR="DarkRed"]${offset 10}[/COLOR]$color8 /$color3 System$color8 /
[COLOR="#8b0000"]${offset 10}[/COLOR]$color2 $sysname$color9 -$color2 $machine
[COLOR="#8b0000"]${offset 10}[/COLOR]$color2 $kernel
[COLOR="#8b0000"]${offset 10}[/COLOR]$color2 CrunchBang$color9 on$color2 $nodename
[COLOR="#8b0000"]${offset 10}[/COLOR]$color6 ${time %A %d/%m/%y %kh%M}
[COLOR="#8b0000"]${offset 10}[/COLOR]$color2 Uptime :$color6 $uptime

[COLOR="#8b0000"]${offset 10}[/COLOR]$color8 /$color3 Mails$color8 /
[COLOR="#8b0000"]${offset 15}[/COLOR]$color2 arpbook : $color4${imap_unseen mail.mac.com "adresse mac" "mot de passe mac"}
[COLOR="#8b0000"]${offset 15}[/COLOR]$color2 larnel  : $color4${imap_unseen mail.mac.com "adresse mac" "mot de passe mac"}
```
By adding 70 to each highlighted offset. Increase or decrease 70 to your need.
eg the first one becomes```
${offset 80}
```
One hellova fullscreen conky to mess with.
I would have split it up into three or four conkys.
Arranging horizontally(offset) is ok but if you want to arrange vertically (voffset)
it becomes hard because it will also move the code that follows.

P.S. To easily find a post use thread tools and subscribe to the thread.
    Then use Quick Links > Subscribed Threads

---

### Post by Ultra_Man on 2009-12-29
Thanks. I was able to make it nearly perfect now.
[http://i.neoseeker.com/mgv/350752-Bass%20Ultra/752/20/december_29_09.png](http://i.neoseeker.com/mgv/350752-Bass%20Ultra/752/20/december_29_09.png)
Now, I need to know how to get temp readings. D:

You can see I have it on there, but its not showing any numbers. D:

---

### Post by stinkeye on 2009-12-29
> **Ultra_Man said:**
> Thanks. I was able to make it nearly perfect now.
[http://i.neoseeker.com/mgv/350752-Bass%20Ultra/752/20/december_29_09.png](http://i.neoseeker.com/mgv/350752-Bass%20Ultra/752/20/december_29_09.png)
Now, I need to know how to get temp readings. D:

You can see I have it on there, but its not showing any numbers. D:

You need to install hddtemp. It's in synaptic.

[_**[COLOR="DarkRed"]HOW TO: A Beginners Guide to Setting up Conky[/COLOR]**_]("http://ubuntuforums.org/showpost.php?p=5436679&postcount=1")

---

### Post by Ultra_Man on 2010-01-08
So, I got rid of conky a while ago, after it not showing up on my multi wallpaper workspace. 

Now, I changed back to good old one wallpaper, installed conky, checked my .conkyrc, but its not showing up. I'm using nautilus to draw the desktop, but its not drawing the icons either, so could that be a problem?

---

### Post by stinkeye on 2010-01-08
> **Ultra_Man said:**
> So, I got rid of conky a while ago, after it not showing up on my multi wallpaper workspace. 

Now, I changed back to good old one wallpaper, installed conky, checked my .conkyrc, but its not showing up. I'm using nautilus to draw the desktop, but its not drawing the icons either, so could that be a problem?
How are you starting conky?
Are you using the same conky as before?
Start in terminal and see what errors you get.

---

### Post by haggus on 2011-01-06
Do yo u have this line in your .conkyrc?

```
# Create own window instead of using desktop (required in nautilus)
own_window no
```

your answer would be [COLOR="Red"]**yes**[/COLOR] I think if using nautilus.

---

