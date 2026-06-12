---
title: "fluxbox configurations"
date: 2008-03-09
forum: Desktop Environments
---

### Post by jorik42 on 2008-03-09
hey all, i really enjoy fluxbox, but i have some questions on how to configure it.  

[http://www.abclinuxu.cz/images/clanky/hradilek/fluxbox.png](http://www.abclinuxu.cz/images/clanky/hradilek/fluxbox.png)

in the picture in the link, in the upper left is a printout of sorts displaying cpu load and network information.  my question is how does one set this up?  id really like to have something of this nature.  

any ideas?

jorik

---

### Post by PurposeOfReason on 2008-03-09
That is a program called conky. There is a whole tread on configurations for it. Install conky and then edit the ~/.conkyrc file to your needs.

[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

---

### Post by jorik42 on 2008-03-10
ok, so ive installed conky and have played around with installing it.  however, theres one thing that annoys me.  whenever i drag a program window over conky, the portion of conky that was covered up get erased for a few seconds.  is there a way to make it so that this doesnt happen?

my conkyrc code is:

background yes
use_xft yes
xftfont HandelGotD:size=8
xftalpha 0.1
update_interval 0.1
total_run_times 0
own_window no
#own_window_type normal
#own_window_transparent yes
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 200 5
maximum_width 200
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color white
default_shade_color red
default_outline_color green
alignment top_right
gap_x 18
gap_y 48
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 1
override_utf8_locale no
use_spacer yes

TEXT
$sysname $kernel $alignr $machine
Intel Centrino Duo $alignr${freq_g cpu0}Ghz
Uptime $alignr $uptime
Hostname $alignr $nodename
${cpugraph cpu0 16,200 ffffff ffffff}
CPU:1  ${cpu cpu1}% ${cpubar cpu1}
CPU:2  ${cpu cpu2}% ${cpubar cpu2}

MEM $alignc $mem / $memmax $alignr $memperc%
$membar

/home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
${fs_bar /home}

Processes 
$alignr $running_processes Running 
$alignr $processes Sleeping

Top Processes

CPU $alignr CPU% MEM%
    ${top name 1}$alignr${top cpu 1}${top mem 1}
    ${top name 2}$alignr${top cpu 2}${top mem 2}
    ${top name 3}$alignr${top cpu 2}${top mem 3}

MEM $alignr CPU% MEM%
    ${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
    ${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}
    ${top_mem name 3}$alignr${top_mem cpu 3}${top_mem mem 3}

Connections ${tcp_portmon 32768 61000 count} ${alignr} Service/Port

${tcp_portmon 32768 61000 rhost 0} ${alignr} ${tcp_portmon 32768 61000 rservice 0}
${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice 1}
${tcp_portmon 32768 61000 rhost 2} ${alignr} ${tcp_portmon 32768 61000 rservice 2}
${tcp_portmon 32768 61000 rhost 3} ${alignr} ${tcp_portmon 32768 61000 rservice 3}
${tcp_portmon 32768 61000 rhost 4} ${alignr} ${tcp_portmon 32768 61000 rservice 4}
${tcp_portmon 32768 61000 rhost 5} ${alignr} ${tcp_portmon 32768 61000 rservice 5}


any ideas would be appreciated.

jorik

---

### Post by rjmdomingo2003 on 2008-03-10
> **jorik42 said:**
> ok, so ive installed conky and have played around with installing it.  however, theres one thing that annoys me.  whenever i drag a program window over conky, the portion of conky that was covered up get erased for a few seconds.  is there a way to make it so that this doesnt happen?

my conkyrc code is:

background yes
use_xft yes
xftfont HandelGotD:size=8
xftalpha 0.1
update_interval 0.1
total_run_times 0
own_window no
#own_window_type normal
#own_window_transparent yes
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 200 5
maximum_width 200
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color white
default_shade_color red
default_outline_color green
alignment top_right
gap_x 18
gap_y 48
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 1
override_utf8_locale no
use_spacer yes

TEXT
$sysname $kernel $alignr $machine
Intel Centrino Duo $alignr${freq_g cpu0}Ghz
Uptime $alignr $uptime
Hostname $alignr $nodename
${cpugraph cpu0 16,200 ffffff ffffff}
CPU:1  ${cpu cpu1}% ${cpubar cpu1}
CPU:2  ${cpu cpu2}% ${cpubar cpu2}

MEM $alignc $mem / $memmax $alignr $memperc%
$membar

/home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
${fs_bar /home}

Processes 
$alignr $running_processes Running 
$alignr $processes Sleeping

Top Processes

CPU $alignr CPU% MEM%
    ${top name 1}$alignr${top cpu 1}${top mem 1}
    ${top name 2}$alignr${top cpu 2}${top mem 2}
    ${top name 3}$alignr${top cpu 2}${top mem 3}

MEM $alignr CPU% MEM%
    ${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
    ${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}
    ${top_mem name 3}$alignr${top_mem cpu 3}${top_mem mem 3}

Connections ${tcp_portmon 32768 61000 count} ${alignr} Service/Port

${tcp_portmon 32768 61000 rhost 0} ${alignr} ${tcp_portmon 32768 61000 rservice 0}
${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice 1}
${tcp_portmon 32768 61000 rhost 2} ${alignr} ${tcp_portmon 32768 61000 rservice 2}
${tcp_portmon 32768 61000 rhost 3} ${alignr} ${tcp_portmon 32768 61000 rservice 3}
${tcp_portmon 32768 61000 rhost 4} ${alignr} ${tcp_portmon 32768 61000 rservice 4}
${tcp_portmon 32768 61000 rhost 5} ${alignr} ${tcp_portmon 32768 61000 rservice 5}


any ideas would be appreciated.

jorik
If you run conky through the terminal, you should

```
$ conky &
```

then

```
$ exit
```

To include it in the startup file,

```
conky &
```

Hope this helped.

---

### Post by jorik42 on 2008-03-12
well, at first the above solution seemed to do the trick; however, it is occuring again.  whenever i cover part of the conky display on the desktop, it gets blacked out when the application box/window is moved.  

any ideas as to what is causing this, if not any solutions?  my conkyrc code is in my above post, and hasnt changed at all.  

also, how would i include the  code "conky &" in the startup?  is there a text file that i edit for that?  where would that be found..?

thanks, 
   jorik

---

### Post by RedSquirrel on 2008-03-12
For Fluxbox, put the "conky &" in the text file ~/.fluxbox/startup.

I'm not sure if it will help, but I use these in my .conkyrc: 

```
own_window yes
own_window_type normal
```[http://conky.sourceforge.net/faq.html](http://conky.sourceforge.net/faq.html)

There are some links at the bottom of that page (two of them for these forums!).

When you run conky in a terminal, do you get any errors or warnings?

---

### Post by jorik42 on 2008-03-12
thanks for the help

it turns out that i didnt have double buffering enabled in my xorg.conf file.  once i fixed that,  it seems to work just fine now.  :D

EDIT: i take that back; it works fine when you put terminal windows over it.  but other windows still cause it to dissappear.  ill try poking around a bit more, see i anything else turns up.  


jorik

---

### Post by jorik42 on 2008-03-12
based on futher experimentation, it seems that logging into gnome is what is causing my conky to screw up.  

when i restart my computer (not merely my x server), and log into fluxbox, all is well.  same goes if i log out of flux and log back into it.  still no problems.  however, if i log out of flux and into gnome, then back into flux, conky is screwed up.  

any ideas as to why this might be? 


thanks, 
    jorik

---

### Post by spupy on 2008-03-12
> **jorik42 said:**
> based on futher experimentation, it seems that logging into gnome is what is causing my conky to screw up.  

when i restart my computer (not merely my x server), and log into fluxbox, all is well.  same goes if i log out of flux and log back into it.  still no problems.  however, if i log out of flux and into gnome, then back into flux, conky is screwed up.  

any ideas as to why this might be? 
Are you running Compiz in Gnome?

---

### Post by jorik42 on 2008-03-12
yeah; though i cant recall if i have it disabled at the moment or not.  do you think that compiz is causing the problem?

jorik

---

