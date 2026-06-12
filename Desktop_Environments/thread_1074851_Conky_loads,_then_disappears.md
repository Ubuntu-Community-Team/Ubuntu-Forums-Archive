---
title: "Conky loads, then disappears"
date: 2009-02-19
forum: Desktop Environments
---

### Post by WildeBeest on 2009-02-19
Conky starts when I reboot, then disappears from the desktop. It only display on desktop 1.

I have desktop effects enabled, 4 desktops and cube.

Not sure when it disappears, it seems like after an application covers it.

Any help would be appreciated.

---

### Post by WildeBeest on 2009-02-20
Anyone?

---

### Post by Rizlaw on 2009-02-20
> **WildeBeest said:**
> Conky starts when I reboot, then disappears from the desktop. It only display on desktop 1.

I have desktop effects enabled, 4 desktops and cube.

Not sure when it disappears, it seems like after an application covers it.

Any help would be appreciated.

WildeBeest, your post is a trifle confusing "when I reboot, [Conky] disappears from the desktop." Then you say, "It only display on desktop 1."  Which is it?

In any event, to install Conky and have it "reappear" on each reboot, my advice is as follows:

To have Conky start automatically on login:

1. In your /home/WildeBeest/ folder open "gedit" and create a small script file named:      .conky_start.sh

Notes:
a. wherever "WildeBeest" appears substitute your login name 
b. the period in the filename is important and also makes the file a hidden file.

2. Into the script file type or paste the following code:

#!/bin/bash
sleep 10 && conky;


The above two lines of code will start Conky 10 seconds after logging in.


3. Make the script executable by opening a Terminal window in the same folder as the bash script you created and saved to your /Home/WildeBeest/ folder, and in the Terminal window type:

chmod a+x .conky_start.sh

This will make the ".conky_start.sh" file executable.

4. Finally, go to SYSTEM > SESSION > STARTUP PROGRAMS and add a new command:   /home/WildeBeest/.conky_start.sh

You can give it a "Name" of Conky Startup if you like. The imporant part is to enter the above command into the command field and save it. Remember to substitute your login name for "WildeBeest".

   Conky will now start automatically with each new login.

Hope this helps and solves your problem.

---

### Post by WildeBeest on 2009-02-21
@Rizlaw

I had already done everything you suggested.

I guess I could have been clearer.

After login, Conky displays, but only on Desktop1. Shouldn't it appear on all 4 Desktops?
I switch away from Desktop1, when I return to Desktop1 and click show Desktop, conky is gone.
I have different apps on each Desktop. Firefox on 1 & 2, Thunderbird and Opera on 3, Pidgin and skype on 4. I also have a couple of terminal sessions and instances of nautilus running.

---

### Post by Rizlaw on 2009-02-21
> **WildeBeest said:**
> @Rizlaw

I had already done everything you suggested.

I guess I could have been clearer.

After login, Conky displays, but only on Desktop1. Shouldn't it appear on all 4 Desktops?
I switch away from Desktop1, when I return to Desktop1 and click show Desktop, conky is gone.
I have different apps on each Desktop. Firefox on 1 & 2, Thunderbird and Opera on 3, Pidgin and skype on 4. I also have a couple of terminal sessions and instances of nautilus running.

I'm not sure I can offer more help, except to say that, I am using Ubuntu 8.10, which has newer packages than your 8.04 LTS. I assume you are using Compiz by default, as I am. I have dual 24" monitors running off an Nvidia 7950GT video card, and I have no problem seeing my Conky overlay on the far right hand side of my 2nd 1920x1200 monitor (using Twinview setting which equals a 3840x1200 desktop). I can spin my Compiz cube and see Conky on all 4 sides/desktops of the cube. If I turn Compiz off, I still see Conky on all 4 desktops.

Since I don't know your exact hardware/software set-up, it's hard to say more. If you have customised your "Conkyrc" file, you might compare it against someone else's file to see if you have added or changed a setting which might account for your peculiar problem. I don't think the programs you have running on each desktop have anything to do with the problem. It could be the desktop your running: KDE4.x, Fluxbox, etc.

I suggest you look at the following links for more info and help:

Conky FAQ at: [http://conky.sourceforge.net/faq.html](http://conky.sourceforge.net/faq.html) 
Linux.com Expert's Guide to Conky: [http://www.linux.com/feature/136147](http://www.linux.com/feature/136147)

---

### Post by cubeist on 2009-02-21
can you post your conkyrc file please... mine loads on all four sides of the cube and I actually only want it on one desktop... so I will compare my conkyrc with yours and see if we can both get the ideal setup...

As you probably know, your conkyrc is in your home folder and it is actually called ".conkycr"

---

### Post by WildeBeest on 2009-02-21
My graphics ccard is a 8400gs, driver 180.29, 20" lcd monitor.

Conky file:

```
background yes
cpu_avg_samples 2
net_avg_samples 2
out_to_console no
text_buffer_size 2048
max_user_text 16384
max_specials 5120
use_xft yes
xftfont monospace-9
own_window_transparent yes
own_window_colour hotpink
xftalpha 0.8
mail_spool $MAIL
update_interval 1
own_window yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_type override
double_buffer yes
minimum_size 120 5
maximum_width 270
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
stippled_borders 0
border_margin 10
border_width 1
default_color white
default_shade_color white
default_outline_color white
alignment top_right
gap_x 5
gap_y 20
use_spacer left
no_buffers yes
uppercase no

TEXT

${font EmpireState:size=16}{SYSTEM} ${hr 2}
${voffset 2}${font StyleBats:size=16}i${font}   Kernel:  ${alignr}${kernel}
${font StyleBats:size=16}A${font}   CPU: ${alignr}${cpu cpu1}% ${alignr}${cpubar cpu1 8,80}
${font StyleBats:size=16}g${font}   RAM: ${alignr}$memperc% ${alignr}${membar 8,80}
${font StyleBats:size=16}j${font}   SWAP: ${alignr}$swapperc% ${alignr}${swapbar 8,80}
${font StyleBats:size=16}8${font}   Load: ${alignr}$loadavg
${font StyleBats:size=16}q${font}   Uptime: ${alignr}${uptime}

${font EmpireState:size=16}{PROCESSES} ${hr 2}${font}
NAME $alignr PID    CPU    MEM
${top name 1} $alignr ${top pid 1} ${top cpu 1} ${top mem 1}
${top name 2} $alignr ${top pid 2} ${top cpu 2} ${top mem 2}
${top name 3} $alignr ${top pid 3} ${top cpu 3} ${top mem 3}
${top name 4} $alignr ${top pid 4} ${top cpu 4} ${top mem 4}
${top name 5} $alignr ${top pid 5} ${top cpu 5} ${top mem 5}

${font EmpireState:size=16}{DRIVE} ${hr 2}${font}
${voffset 2}${font Pie charts for maps:size=14}1${font}   ${voffset -5}Home:
${voffset 4}${fs_used /home}/${fs_size /home} ${alignr}${fs_free_perc /home}% ${fs_bar 8,80 /home}
${font Pie charts for maps:size=14}1${font}   ${voffset -5}Html:
${voffset 4}${fs_used /media/disk-1}/${fs_size /media/disk-1} ${alignr}${fs_free_perc /media/disk-1}% ${fs_bar 8,80 /media/disk-1}
${font Pie charts for maps:size=14}1${font}   ${voffset -5}Torrent:
${voffset 4}${fs_used /media/disk}/${fs_size /media/disk} ${alignr}${fs_free_perc /media/disk}% ${fs_bar 8,80 /media/disk}

${font EmpireState:size=16}{NETWORK} ${hr 2}${font}
${voffset 2}${font OpenSymbol:size=14}&#59017;${font}   Up: ${alignr}${upspeed eth0} kb/s ${upspeedgraph eth0 8,100 104E8B 0077ff 45}
${voffset 4}${font OpenSymbol:size=14}&#59013;${font}   Down: ${alignr}${downspeed eth0} kb/s ${downspeedgraph eth0 8,100 104E8B 0077ff 450}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup eth0}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown eth0}
${voffset 4}${font StyleBats:size=16}l${font}   Ip: ${addr eth0}  ~ ${texeci 3600 wget http://checkip.dyndns.org -O - -o /dev/null | cut -d : -f 2 | cut -d \< -f 1}

${execi 30 netstat -ept | grep ESTAB | awk '{print $9}' | cut -d: -f1 | sort | uniq -c | sort -nr}

${execi 30 tail -n3 /var/log/messages | awk '{print " ",$5,$6,$7,$8,$9,$10}' | fold -w50}

${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
```

---

### Post by cubeist on 2009-02-21
change "own_window_type override" to "own_window_type normal" and this should fix your problem

---

### Post by WildeBeest on 2009-02-22
Thanks, I'll give it a shot.

---

### Post by WildeBeest on 2009-02-22
Now it works for Desktop 1, how do I get it to display on the other 3?

---

