---
title: "issue with conky when logging in"
date: 2010-02-26
forum: Desktop Environments
---

### Post by gixpaulie on 2010-02-26
Hi all,

I have setup conky to startup at boot with the gnome-session-properties, when i login the splash screen comes up with the loading bar then a little while after conky starts has planned but once the splash screen goes away conky disappears off the desktop :confused:

any ideas why this is 


ps its on 9.10

thanks

---

### Post by Brandon Williams on 2010-02-26
The common approach is to use a startup script that delays launch of conky until the desktop manager is fully initialized. [Here is a related thread](http://ubuntuforums.org/showthread.php?t=550378)

If that doesn't solve the problem, then post more info about how you start conky and also post your .conkyrc.

---

### Post by gixpaulie on 2010-02-26
Hi Brandon,

Thanks i will try that , but i have tried to adjust the config.conf in all different ways and it still disappears so i think your first option will be the best bet.

thanks again

---

### Post by gixpaulie on 2010-02-26
i have tried that link your put up , also running the conky command though the rc.local and conky still loads over the top of the login box with the loadbar then when that goes conky goes ](*,)](*,)](*,)

---

### Post by gixpaulie on 2010-02-26
oh heres whats in my conky.conf

own_window yes
own_window_transparent yes
own_window_type override
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
alignment top_right
border_width 0
cpu_avg_samples 2
default_color green
default_outline_color green
default_shade_color green
draw_borders no
draw_graph_borders no
draw_outline no
draw_shades no
use_xft yes
xftfont DejaVu Sans Mono:size=10
gap_x 0
gap_y 0
minimum_size 5 5
net_avg_samples 2
out_to_console no
out_to_stderr no
extra_newline no
own_window_class Conky
stippled_borders 0
update_interval 1.0
uppercase no
use_spacer none
show_graph_scale no
show_graph_range no

---

### Post by gixpaulie on 2010-02-26
and now the rc.local is not running help !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by Brandon Williams on 2010-02-27
You don't want to start conky from rc.local. It runs as a regular user and should be configured as a gnome startup application. The posts in the thread I linked to suggest writing a script that will delay for 10 to 20 seconds before starting conky, and using that as a startup application in the gnome configuration.

---

### Post by gixpaulie on 2010-02-27
Thanks Brandon that worked brillaintly. I dont know what i have done i run a command that just echo's text into a file and that was working now the rc.local dont run at boot. I have checked the permission of the files there fine and run /etc/rc.local and /etc/inti.d/rc.local manualy which works so it looks like the /etc/init.d/rc.local isnt running as this tells the /etc/rc.local to run. What tells the /etc/init.d/rc.local start to run?? 

Thanks for your help

---

### Post by gixpaulie on 2010-02-27
Dont worry i have sorted it . I checked all the runlevel files and /etc/init.d/rc.local was in them all, so i just did update-rc.d -f rc.local remove then update-rc.d -f rc.local defaults and its sorted :p

Thanks again for all your help!

---

