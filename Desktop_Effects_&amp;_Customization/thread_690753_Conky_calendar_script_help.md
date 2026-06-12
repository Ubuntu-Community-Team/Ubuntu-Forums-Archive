---
title: "Conky calendar script help"
date: 2008-02-07
forum: Desktop Effects &amp; Customization
---

### Post by ed-koala on 2008-02-07
I'm currently running Conky with a calendar script I got off the web.  My problem is I want to center the calendar, but if I put $alignc in front all it centers is the name of the month, not the rest of the calendar.  Here is the script call in Conky:

*${color lightgrey}${alignc}${execi 1 ~/Desktop/conky_scripts/calendar.sh first_part}${color #ddaa00}${execi 1 ~/Desktop/conky_scripts/calendar.sh today }${color }${execi 1 ~/Desktop/conky_scripts/calendar.sh second_part}*

And the script is:

[I]#! /bin/sh
#str=`echo '\033[01;32m29'`

DATE=`date | awk -F" " '{print $3}'`

case "$1" in
first_part)
cal | grep '[a-zA-Z]';
cal | grep -v '[a-zA-Z]' | grep '[0-9]' | awk -F$DATE ' BEGIN {i=0}
($1 == $0 && i==0) {print $1}
($1 != $0 && i==0){i=i+1;print $1}';
;;
today)
echo $DATE;
;;
second_part)
cal | grep -v '[a-zA-Z]' | grep '[0-9]' | awk -F$DATE ' BEGIN {i=1}
(i==0) {print $0}
($1 != $0 && i==1){i=i-1;print $2}
';
;;
esac[/I]

I'm hoping for a solution . . . I can't find one anywhere.

---

### Post by MeKino on 2008-05-17
I had exactly the same problem.

The original script had "use_xft yes" which does something to the font size and appearance.

setting "use_xft no" aligned the calendar properly but wouldn't load the font set in the script.

The solution I found was to run a separate conky script for the calendar (easy to do) but without using any xft settings.

Here's my script. You can see xft commented out. The calendar appears top left of screen.

background yes
#use_xft no aligns calendar
use_xft no
#xftfont Sans:size=6
#xftalpha 0.9
#font Sans:size=8
update_interval 300
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_colour grey
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 250 5
maximum_width 120
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
default_color blue
default_shade_color black
default_outline_color green
alignment top_center
gap_x 5
gap_y 32
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no
uppercase yes # set to yes if you want all text to be in uppercase
# maintain spacing between certain elements: left, right or none
use_spacer left
TEXT
${color #0077ff}Calendar ${hr 1}${color}
${color blue}${execi 1 ~/.conky/get_calendar.sh first_part}${color red}${execi 1 ~/.conky/get_calendar.sh today }${color blue}${execi 1 ~/.conky/get_calendar.sh second_part}

---

### Post by gaijindewanai on 2008-06-12
can you tell me where can I get the script?
I tried your script but it doesn't appear in my conky..

---

### Post by MeKino on 2008-06-12
My calendar script is exactly the same as yours so I can confirm it works ok but I need to run 2 conky files, one for system details and one for the calendar.

My conky file is this:

#!/bin/bash 
sleep 15 && exec conky -d -c ~/conkyrc & sleep 17 && exec conky -d -c ~/.conkyrc2 & exit

conkyrc is my system display
conkyrc2 is my calendar display and consists of the script in my previous post which call the calendar.sh

p.s. I have also found the need to set 
text_buffer_size 256
in my conkrc2 or else it all gets squashed up

---

### Post by gaijindewanai on 2008-06-13
hmmm...
i only use:
${exec cal}

its work rite now.
but i have another question,
I can display last month and this month, or this month and next month on the same row, but I cant display last month and next month on the same row.. can u help me with the script?

---

### Post by hailukah on 2008-07-07
I have been working on this problem for a few weeks now and I think I have all of the bugs worked out.  Here's how I added a calendar to conky.

First I'm using Conky 1.5.1.  I compiled it from source because I'm using Fluxbuntu which is currently based on Gutsy which used an older version that didn't support ${execpi}.  ${execpi} tells conky to parse the output from a script or other exec.  This allows us to include things like color and justification.

Here's the command if you want to copy and paste:

```
${font Aerial:style=Bold:pixelsize=14}${execi 60 date +"%B %Y" | tr "[:lower:]" "[:upper:]"}${font Snap.se:size=8} ${hr 1 }

${font Bitstream Vera Sans Mono:style=Bold:size=13}${execpi 60 DJS=`date +%_d`; cal | sed '1d' | sed '/./!d' | sed 's/$/                     /' | fold -w 21 | sed -n '/^.\{21\}/p' | sed 's/^/${alignc} /' | sed /" $DJS " s/" $DJS "/" "'${color1}'"$DJS"'${color0}'" "/}
```

You must set
```
text_buffer_size 256
```
for the calendar to display.

That first line gives me the month and year (+%B %Y) formatted to match the other elements in my conkyrc.  Piping date through tr "[:lower:]" "[:upper:]" changes the month to all uppercase.

The second line is a bit more complex.  It has taken time but I think I it is free of bugs, though I'm sure it could be shortened or sped up, but I haven't had any problems with execution speed.  YMMV.

Now for a step by step of what the code does:

```
${font Bitstream Vera Sans Mono:style=Bold:size=13}
```
This sets the font to fixed.  This is rather important so that all of the dates line up.

```
${execpi 60
```
Tells conky to exec the following code every 60 seconds and parse the output.

```
DJS=`date +%_d`;
```
DJS just stands for Date and my initials.  date +%_d gives us todays date space padded.  The space padding is important so that later we won't be identifying all 2s in the calendar when the date is the 2nd.  We will be searching for $DJS later in the script, that is today's date.

```
cal
```
The linux calendar.

```
sed '1d'
```
Deletes the first line, which is the month and year.

```
sed '/./!d'
```
Passes only non-blank lines.  Conky pays attention to blank lines for it's formatting, this will keep the calendar from taking too much space.

```
sed 's/$/                     /' | fold -w 21 | sed -n '/^.\{21\}/p'
```
I was having trouble getting the calendar centered because the last line of the calendar is usually shorter than the other lines.  This is a hack of a work around, but it is all I've been able to come up with.

The first sed adds 21 spaces to the end of each line.  fold -w 21 wraps each line at 21 spaces. The second sed only prints lines at least 21 characters long.  Now our last line will be space padded to the end of the line.  Now we're ready for:

```
sed 's/^/${alignc} /'
```
This adds ${alignc} and a space to the beginning of each line.  This will center our calendar in conky.  The space is important in that we will be searching for todays date with spaces on both sides.

```
sed /" $DJS " s/" $DJS "/" "'${color1}'"$DJS"'${color0}'" "/
```
This finds the line with today's date and then adds color to the date.  The ${color1} & ${color0} are set in the top section of conkyrc around text_buffer_size 256.  Here's my .conkyrc

```
background yes
#font Snap.se:size=8
#xftfont Snap.se:size=8
use_xft yes
xftalpha 0.1
update_interval 5.0
total_run_times 0
#own_window yes
#own_window_type override
#own_window_transparent yes
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
minimum_size 206 5
maximum_width 206
default_color ffffff
default_shade_color 000000
default_outline_color 000000
alignment middle_right
gap_x 6
gap_y 22
no_buffers yes
cpu_avg_samples 2
override_utf8_locale no
uppercase no # set to yes if you want all text to be in uppercase
use_spacer none
color0 FFFFFF
color1 AFAFFF
text_buffer_size 256


TEXT
${font Aerial:style=Bold:pixelsize=14}${execi 60 date +"%B %Y" | tr "[:lower:]" "[:upper:]"}${font Snap.se:size=8} ${hr 1 }

${font Bitstream Vera Sans Mono:style=Bold:size=13}${execpi 60 DJS=`date +%_d`; cal | sed '1d' | sed '/./!d' | sed 's/$/                     /' | fold -w 21 | sed -n '/^.\{21\}/p' | sed 's/^/${alignc} /' | sed /" $DJS "/s/" $DJS "/" "'${color1}'"$DJS"'${color0}'" "/}

${font Aerial:style=Bold:pixelsize=14}SYSTEM${font Snap.se:size=8} ${hr 1 }

Hostname: $alignr$nodename
Kernel: $alignr$kernel
Uptime: $alignr$uptime
Processes: ${alignr}$processes ($running_processes running)
Load: ${alignr}$loadavg


CPU       ${alignc} ${freq}MHz ${alignr}(${cpu cpu1}%)
${cpubar 4 cpu1}
${cpugraph cccccc ffffff}

RAM ${alignr}$mem / $memmax ($memperc%)
${membar 4}

SWAP ${alignr}$swap / $swapmax ($swapperc%)
${swapbar 4}

Highest CPU $alignr CPU% MEM%
${hr 1}
${top name 1}$alignr${top cpu 1}${top mem 1}
${top name 2}$alignr${top cpu 2}${top mem 2}
${top name 3}$alignr${top cpu 3}${top mem 3}

Highest MEM $alignr CPU% MEM%
${hr 1}
${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}
${top_mem name 3}$alignr${top_mem cpu 3}${top_mem mem 3}



${font Aerial:style=Bold:pixelsize=12}FILESYSTEM ${font Snap.se:size=8}${hr 1}

Root: ${alignr}${fs_free /} / ${fs_size /}
${fs_bar 4 /}

Home: ${alignr}${fs_free /home} / ${fs_size /home}
${fs_bar 4 /home}




${font Aerial:style=Bold:pixelsize=12}NETWORK ${font Snap.se:size=8}${hr 1}

Down ${downspeed eth0} k/s ${alignr}Up ${upspeed eth0} k/s
${downspeedgraph eth0 25,107 cccccc ffffff} ${alignr}${upspeedgraph eth0 25,107 cccccc ffffff}
Total ${totaldown eth0} ${alignr}Total ${totalup eth0}


```

Anyways, hope this will be helpful to some of you.

josh

---

