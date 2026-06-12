---
title: "Conky + antialliasing problem"
date: 2008-03-03
forum: Desktop Effects &amp; Customization
---

### Post by jim_p on 2008-03-03
Hello!

I left my Dapper installation a month ago to move to something more recent, Gutsy that is.

And, being a perfectionist, I got from a server installation to a minimal gnome d.e. to a system that fits my needs and lacks useless stuff like games.

I installed conky, used my old .conkyrc file from Dapper and set it to start upon login to gnome.
My problem is that the fonts are NOT antialliased at first. I have to killall conky and restart it to get the fonts to become smooth.
Here is my .conkyrc```

background yes
use_xft yes
xftfont Verdana:size=11
xftalpha 0.8
update_interval 5.0
total_run_times 0
color1 orange
own_window yes
own_window_type normal
#own_window_colour black
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color white
default_shade_color black
default_outline_color white
alignment bottom_right
cpu_avg_samples 5
override_utf8_locale yes
use_spacer no
gap_y 0
gap_x 0
#maximum_width 1280
#minimum_size 150 5

# USB stick check script
# ${if_mounted /media/usbdisk}USB stick $alignc ${fs_used /media/usbdisk} / ${fs_size /media/usbdisk} $alignr ${fs_free_perc /media/usbdisk}% $else not mounted ${endif}
# Internet ip check 
# ${execi 1800 curl -s http://whatismyip.org/}
# Weather forecast 
# ${execi 900 pymetar LGBL | grep Weather:}
# Calendar (USE ONLY MONOTYPE FONTS)
# ${font DejaVu Sans Mono:size=10}${execi 3600 cal}

TEXT
$alignr ${offset -35}${font Verdana:bold:size=18}${time %H:%M}$font
$alignr ${time %A %d %b. %Y}
$alignr down $color1${downspeed eth0} kb/s$color up $color1${upspeed eth0} kb/s$color
$alignr drive temp $color1${hddtemp /dev/sda}$color // cpu temp $color1${hwmon temp 2}°C$color
$alignr linux $color1${fs_free_perc /}%$color free // windows $color1${fs_free_perc /mnt/windows}%$color free // large $color1${fs_free_perc /mnt/large}%$color free
```

I will post screenshots after next reboot, if requested

---

### Post by erginemr on 2008-03-03
I am no Conky expert, but I suggest you to visit the following very long thread:
[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

and compare your .conkyrc file with the ones and screenshots posted there.

---

### Post by jim_p on 2008-03-03
I have searched this thread and I visit it often for ideas, but no luck.

Thank you.

I forgot to mention that I am not using compiz or something

---

### Post by erginemr on 2008-03-03
Maybe this site will help:
[http://bbs.archlinux.org/viewtopic.php?pid=308266](http://bbs.archlinux.org/viewtopic.php?pid=308266)

With respect to the attached screenshots:

1) I have first tried to change the settings from under Appearance -> Fonts

2) It didn't help with Conky.

3) I have then created the file "~/.Xdefaults" in my home folder as suggested by the link above (It didn't exist before.) and added the following lines:
```
Xft*dpi:                96
Xft*antialias:          true
Xft*hinting:            full
```

4) Restarted X server with Ctrl+Alt+BackSpace to get much smoother Conky fonts.

I hope this will solve your problem.

---

### Post by jim_p on 2008-03-03
Thanks a lot erginemr!!!

I can finally have a smoooooth conky!

And... a new challenge just popped up. When I pressed Ctrl+Alt+Backspace to restart X, everything (conky, gnome, wbar, even the mouse cursors) unloaded and I was left there staring at the wallpaper! It did not go back to gdm :( and the only way out is REISUB. 

I will make a new thread about that, but does enyone know any log files that I can I can check to see what happened?

---

### Post by erginemr on 2008-03-03
As long as you get everything back when you restart the computer, you don't have to bother.

---

### Post by jim_p on 2008-03-03
Oddly, I just found the answer to my Ctrl+Alt+Backspace problem. It is some ati thing running. Killed it, restarted X and everything is ok. 

Even conky reverted itself back to no-antialiasing mode! Why? And all seemed so nice some minutes ago!

---

### Post by erginemr on 2008-03-03
I suggest you to switch off your computer completely now. And then switch it on. If everything is fine as expected, then you are good to go...

---

### Post by jim_p on 2008-03-03
I just rebooted, got to desktop, conky is ugly again.

I got disappointed, restarted X just to see, and conky remained ugly! 
It seems the only solution is to kill it and restart it!

---

### Post by erginemr on 2008-03-03
Sorry, if you are sure that there is still a "~/.Xdefaults" file (with a capital X) inside your home folder with:
```
Xft*dpi:                96
Xft*antialias:          true
Xft*hinting:            full
```
then I am afraid it doesn't work. :( You can check its existence and contents with:
```
cat ~/.Xdefaults
```
from Gnome terminal.

Strangely, it seems to work in my system.

---

### Post by jim_p on 2008-03-03
The file is still there and contains the same text!

I dont know why it stopped working :(

I assume there is a "file" that overrides .Xdefaults, like it happened once with mplayer

---

### Post by jim_p on 2008-03-03
3 hours have passed, I rebooted my pc twice since then and now they show up antialiased! What is going on?

---

