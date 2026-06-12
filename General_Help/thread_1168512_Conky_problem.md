---
title: "Conky problem"
date: 2009-05-24
forum: General Help
---

### Post by Nat04 on 2009-05-24
Hi all,

I've got a problem with conky. It loads up fine and when I mount my 2nd and/or external HDD, the free disk space shows up and I'm happy with it. The problem is that it pushes on the list and as results, the last lines are cut. See attached screenshot.

```
background no
font Sans:size=8
#xftfont Sans:size=10
use_xft yes
xftalpha 0.9
update_interval 1.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 220 5
maximum_width 220
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders yes
default_color white
default_shade_color black
default_outline_color green
alignment top_right
gap_x 12
gap_y 35
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no
uppercase yes # set to yes if you want all text to be in uppercase

TEXT
${color white}SYSTEM ${hr 1}${color}

Hostname: $alignr$nodename
Kernel: $alignr$kernel
Uptime: $alignr$uptime

CPU: ${alignr}${freq} MHz
Processes: ${alignr}$processes ($running_processes running)
Load: ${alignr}$loadavg

CPU ${alignr}${cpu cpu1}%
${cpubar 4 cpu1}

Ram ${alignr}$mem / $memmax ($memperc%)
${membar 4}
swap ${alignr}$swap / $swapmax ($swapperc%)
${swapbar 4}

Disk Usage: ${alignr}

${color white}Ubuntu: $color${fs_free /} of ${fs_size /}
${fs_bar /}${if_existing /media/DISK2_VOL1}
${color white}Windows XP: ${color white}${fs_free /media/DISK2_VOL1} of ${fs_size /media/DISK2_VOL1}
${fs_bar /media/DISK2_VOL1}${endif}${if_existing /media/Iomega}
${color white}Iomega: ${color white}${fs_free /media/Iomega} of ${fs_size /media/Iomega}
${fs_bar /media/Iomega}${endif}

Highest CPU $alignr CPU% MEM%
${top name 1}$alignr${top cpu 1}${top mem 1}
${top name 2}$alignr${top cpu 2}${top mem 2}
${top name 3}$alignr${top cpu 3}${top mem 3}

Highest MEM $alignr CPU% MEM%
${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}
${top_mem name 3}$alignr${top_mem cpu 3}${top_mem mem 3}
```Any thoughts?
Thanks in advance.

---

### Post by VCoolio on 2009-05-24
You can set minimum height, that's the 5 in your "minimum_size 220 5". But it should autoresize the window when new lines are added, don't know why it doesn't. Try setting background yes, it's at first glance the only thing that is different from my setup. It means that the process will be run in background and maybe that frees the way for conky to autoresize, just guessing.
Maybe it has to do with the use_spacer variable, check that out, it's not there in your config, so conky should fall back to default which would be use_spacer right.
Btw, don't know if you want to, but if you want to get rid of the shadows you set that in compiz config settings manager, window decoration plugin, the entry for shadow windows. Fill in: any & !(class=conky)

---

### Post by Nat04 on 2009-05-24
Thanks but... It still bugs. :-?
 And btw, it occurs only when conky is launched at startup. When I launch it manually, it resizes itself as it should. Any help?

---

### Post by m_duck on 2009-05-24
I think another "workaround" is to just put a load of blank lines at the bottom of your .conkyrc. While that will make it take up more space (so potential problem depending on its location and whether you use desktop icons) but it will be the blank lines that end up getting cut off rather than anything important.

---

### Post by VCoolio on 2009-05-24
Then add sleep to a startup script; like this:
```

#!/bin/sh
sleep 20 && conky 

```
make that conky -c /path/to/file if you use an other config file than ~/conkyrc. Save as .sh and point to that script in startup applications like this in the command entry:
sh /path/to/script.sh

---

### Post by Nat04 on 2009-05-24
Delaying at startup didn't help either and well, simply adding blank spaces solved the prob.

Thanks for your help!

---

