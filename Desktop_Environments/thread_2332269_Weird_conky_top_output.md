---
title: "Weird conky top output"
date: 2016-07-29
forum: Desktop Environments
---

### Post by CatKiller on 2016-07-29
Because reasons, I've split up my large conkyrc into separate blocks. Even though it's unchanged from the larger one, the block that prints the output from top doesn't work.

Here it is for reference:
```

${color1}PROCESSES ${hr 2}${color}
${voffset 8}
${alignr}${voffset -28}${offset -232}PID
${alignr}${voffset -28}${offset -116}%CPU
${alignr}${voffset -28}${offset -6}%MEM
${top name 1}
${font Inconsolata Medium:size=9}${alignr}${voffset -28}${offset -232}${top pid 1}
${alignr}${voffset -28}${offset -120}${top cpu 1}
${alignr}${voffset -28}${offset -8}${top mem 1}${font}
${top name 2}
${font Inconsolata Medium:size=9}${alignr}${voffset -28}${offset -232}${top pid 2}
${alignr}${voffset -28}${offset -120}${top cpu 2}
${alignr}${voffset -28}${offset -8}${top mem 2}${font}
${top name 3}
${font Inconsolata Medium:size=9}${alignr}${voffset -28}${offset -232}${top pid 3}
${alignr}${voffset -28}${offset -120}${top cpu 3}
${alignr}${voffset -28}${offset -8}${top mem 3}${font} 
```

As part of the larger setup it works perfectly, but, as far as I can tell, when it's separate it's sorting top by PID, which is... not useful. Weirdly enough, if I set top_cpu_separate to false it seems to put things in the right order.

Does anyone have any idea what might be going on here, and how to fix it?  Conky version is 1.10.1, if that's useful.

Edit: I've tried converting it to the new lua syntax. Didn't help.

---

### Post by gordintoronto on 2016-07-30
What are you trying to display?

---

### Post by CatKiller on 2016-07-31
> **gordintoronto said:**
> What are you trying to display?
??
The output from top.

---

### Post by Frogs Hair on 2016-08-01
As a second .conkyrc the syntax displayed is incomplete. There are no parameters for size, placement, font, and so on.

---

### Post by CatKiller on 2016-08-01
Yes. There's no point posting the whole thing. The headers are identical other than margin for obvious reasons.

---

### Post by Frogs Hair on 2016-08-01
Are they designated conkyrc1 and conkyrc2.

Example start script.


```
#!/bin/sh
sleep 5
conky -q -c /home/YOURUSERNAME/.conky/conky1/conkyrc1 &
conky -q -c /home/YOURUSERNAME/.conky/conky2/conkyrc2 & exit
```

---

### Post by CatKiller on 2016-08-01
I know how to run conky. I know how to run multiple instances of conky. I know how to set conky up. Identical calls to conky's top object are giving differing outputs for reasons I can't fathom. That's what I was looking for insight into.

---

### Post by CantankRus on 2016-08-01
That section of your conky has numerous negative voffsets to position the output in your original config.
When I run your posted conkyrc section the output disappears because of negative voffsets.
[ATTACH=CONFIG]270522[/ATTACH]

Try creating an entirely new config without the voffsets.
...or create a simple top output conkrc and test that.

Here is a basic cpu and ram conky you can test, which uses the **top name** variable. It's in the new lua format.
```
conky.config = {
--###
--# Use XFT? Required to Force UTF8 (see below).

	use_xft = true,
	font = 'Ubuntu Mono:bold:size=12',
	xftalpha = 0.8,
	text_buffer_size = 1024,

--###
--# Force UTF8? Requires XFT (see above).
--# Displays degree symbol, instead of Â°, etc.

	override_utf8_locale = true,

--###
--# Daemonize Conky, aka 'fork to background'.

	background = false,

--###
--# Update interval in seconds.

	update_interval = 3.0,

--###
--# This is the number of times Conky will update before quitting.
--# Set to zero to run forever.

	total_run_times = 0,

--###
--# Create own window instead of using desktop (required in nautilus)?

	own_window = true,
	own_window_colour = 'blue',--# use gtk-theme-config to set unity panel color then use gcolor2 eyedropper to get your panel color
	own_window_type = normal,
	own_window_transparent = false,
	own_window_hints = 'undecorated,sticky,skip_taskbar,skip_pager,below',
	default_color = 'white',
--	own_window_argb_visual = false,--# change to no if problems
--	own_window_argb_value = 255,

--###
--# Use double buffering? Reduces flicker.

	double_buffer = true,

--###
--# Draw shades?

	draw_shades = false,
	default_shade_color = '#000000',

--###
--# Draw outlines?

	draw_outline = false,
--default_outline_color 000000

--###
--# Draw borders around text?

	draw_borders = false,

--###
--# Draw borders around graphs?

	draw_graph_borders = false,

--###
--# Print text to stdout?
--# Print text in console?

	out_to_ncurses = false,
	out_to_console = false,

--###
--# Text alignment.

	alignment = 'top_right',

--###
--# Minimum size of text area.

	minimum_width = 300, minimum_height = 100,
	maximum_width = 300,

--###
--# Gap between text and screen borders.

	gap_x = 10,
	gap_y = 50,

--###
--# Shorten MiB/GiB to M/G in stats.

	short_units = true,

--###
--# Pad % symbol spacing after numbers.

	pad_percents = 0,

--###
--# Pad spacing between text and borders.

	border_inner_margin = 0,
	border_outer_margin = 0,
	border_width = 0,

--###
--# Limit the length of names in "Top Processes".

	--top_name_width = 10,

--###
--# Subtract file system -/+buffers/cache from used memory?
--# Set to yes, to produce meaningful physical memory stats.

	no_buffers = true,

--###
--# Set to yes, if you want all text to be in UPPERCASE.

	uppercase = false,

--###
--# Number of cpu samples to average.
--# Set to 1 to disable averaging.

	cpu_avg_samples = 2,

--###
--# Number of net samples to average.
--# Set to 1 to disable averaging.

	net_avg_samples = 2,

--###
--# Add spaces to keep things from moving around?
--# Only affects certain objects.

	use_spacer = 'right',

--###
--# My colors (suit yourself).

	color0 = 'White',
	color1 = 'Ivory',
	color2 = 'Ivory2',
	color3 = 'Ivory3',
	color4 = '#FF4040',
	color5 = '#FCE3BB',--text colour
	color6 = 'Gray',
	color7 = 'AntiqueWhite4',
	color8 = '#F9A41E',
--color9 red
	color9 = '#FFDB58',--icon

};

conky.text = [[
#Top 4 Processes
${font}${goto 32}${voffset 1}Highest: ${alignr 50}CPU${alignr}RAM
${goto 32}${voffset -5.5}${hr 1}
${goto 32}${top name 1} ${goto 180}${top cpu 1}${alignr }${top mem 1}
${goto 32}${top name 2} ${goto 180}${top cpu 2}${alignr }${top mem 2}
${goto 32}${top name 3} ${goto 180}${top cpu 3}${alignr }${top mem 3}
${goto 32}${top name 4} ${goto 180}${top cpu 4}${alignr }${top mem 4}
]];
```

---

### Post by CatKiller on 2016-08-02
The voffsets will make no difference. Why would you think they would? The longer conky script has exactly the same offsets, and the exact same code block produces a differently-ordered top output simply by changing the top_cpu_separate configuration variable. Conky's top object is just broken.

If I needed help with running multiple instances, or positioning things on-screen, that's what I'd have asked about. Seriously.

---

### Post by CantankRus on 2016-08-02
Relax :rolleyes: ... what I was saying is that I can't test your code because the conky snippet you posted doesn't show with all the -voffsets
and I can't be bothered messing around with it to make it show so I can test it.
I don't use top in my conkys.

Give a **simple complete** conkyrc showing top not working as it should and I can test and confirm what you say.

---

### Post by vasa1 on 2016-08-02
CatKiller, two people who are trying to help you have asked for the complete code. Why don't you just oblige?

---

### Post by CatKiller on 2016-08-02
> **vasa1 said:**
> CatKiller, two people who are trying to help you have asked for the complete code. Why don't you just oblige?

Because I'm posting from my phone.

---

### Post by CatKiller on 2016-08-02
> **CantankRus said:**
> Relax :rolleyes: ... what I was saying is that I can't test your code because the conky snippet you posted doesn't show with all the -voffsets
and I can't be bothered messing around with it to make it show so I can test it.
I don't use top in my conkys.

Give a **simple complete** conkyrc showing top not working as it should and I can test and confirm what you say.

Fine. Here are a bunch of instances.

[ATTACH=CONFIG]270534[/ATTACH]

You've got the old massive conky script which is working perfectly. To the left of that you've got the separate one which I've shunted to the left and made not-transparent so that you can see it against the background, and has been converted to the lua format as I said in the first post You'll note that the Processes code block is exactly the same between them, and is as I included in the first post. Below that you've got a new simple version. You'll note that the top output is not ordered by CPU usage as it should be, and top_cpu_separate is set to true, as I said in the first post.

Here is the massive script that works perfectly: ```
# Run Conky in the background
background yes
 
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
#own_window_colour F7F6F5
own_window_type normal
own_window_argb_visual yes
own_window_argb_value 255
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
 
# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes
 
# fiddle with window
use_spacer none

# Use Xft?
use_xft yes
xftfont Bitstream Vera Sans:size=9
#xftfont Futura Md BT Medium:size=9
xftalpha 1.0
text_buffer_size 2048

format_human_readable yes
short_units no
override_utf8_locale yes
 
# Update interval in seconds
update_interval 1
update_interval_on_battery 2
 
# Minimum size of text area
minimum_size 600 5

#Maximum size of text area
#maximum_width 308

# Draw shades?
draw_shades no
 
# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase
 
# Stippled borders?
# stippled_borders 3
 
# border margins
border_inner_margin 0
border_outer_margin 0

# border width
border_width 2
 
# Default colors and also border colors
default_color AEA79F #Warm Grey 5
color1 DD4814 #Ubuntu Orange
color2 95B36A #Green
color3 C0836B #Orange
color4 748B98 #Blue

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
 
# Gap between borders of screen and text
gap_x 12
gap_y 12

top_cpu_separate yes
top_name_width 30

cpu_avg_samples 2
net_avg_samples 2
if_up_strictness link

lua_load ~/.conky/scripts/conky.lua

# stuff after 'TEXT' will be formatted on screen
 
TEXT
${color}
${color1}SYSTEM ${hr 2}${color}
${image ~/.conky/images/computer-laptop.png -p 0,120}
${voffset -26}${texeci 1800 cat /etc/issue.net}
${alignr}${voffset -28}${sysname} ${kernel}
${texeci 1800 cat /etc/os-release | sed -n '2p' | cut -f 2 -d '(' | cut -f 1 -d ')'}
${alignr}${voffset -28}${machine}
${offset 64}${voffset 8}${nodename}
${alignr}${voffset -28}${offset -160}Uptime:
${alignr}${voffset -28}${uptime_short}
${alignr}${offset -160}Governor:
${alignr}${voffset -29}${tail /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 1}

${voffset -28}${color1}CPU ${hr 2}${color}
${image ~/.conky/images/cpu.png -p 0,206}
${voffset -16}${offset 60}${lua_parse context_colour ${hwmon 1 temp 1} ${color4} ${color2} ${color3} 40 64}${color}°C${alignr}${exec cat /proc/cpuinfo | grep 'model name' | uniq | sed -e 's/.*: //' | cut -c 1-26}
${voffset 16}${alignr}${loadgraph 24,600 AEA79F DD4814 4}
${voffset 6}${freq_g 1} GHz:
${alignr}${voffset -28}${offset -416}${lua_parse context_colour ${cpu cpu1} ${color} ${color2} ${color3} 15 50}${color}%
${voffset -28}${offset 192}${cpubar cpu1 12,90}
${freq_g 2} GHz:
${alignr}${voffset -28}${offset -416}${lua_parse context_colour ${cpu cpu2} ${color} ${color2} ${color3} 15 50}${color}%
${voffset -28}${offset 192}${cpubar cpu2 12,90}
${voffset -56}${offset 310}${freq_g 3} GHz:
${alignr}${voffset -28}${offset -100}${lua_parse context_colour ${cpu cpu3} ${color} ${color2} ${color3} 15 50}${color}%
${alignr}${voffset -28}${cpubar cpu3 12,90}
${offset 310}${freq_g 4} GHz:
${alignr}${voffset -28}${offset -100}${lua_parse context_colour ${cpu cpu4} ${color} ${color2} ${color3} 15 50}${color}%
${alignr}${voffset -28}${cpubar cpu4 12,90}

${voffset -16}${color1}DISPLAY  ${hr 2}${color}
${image ~/.conky/images/video-display.png -p 0,392}
${alignr}${voffset -23}${exec lspci | grep VGA | sed -n -e 's/^.*Corporation //p'}
${alignr}${exec xrandr -q | grep "*" | awk '{print $1;}'}

${voffset -28}${color1}MEMORY & STORAGE ${hr 2}${color}
${image ~/.conky/images/gnome-dev-memory.png -p 0,472}
${image ~/.conky/images/drive-harddisk.png -p 300,472}
${voffset -48}${offset 60}${memmax}${alignr}${offset -0}${fs_size /} & ${fs_size /home}
${voffset 10}RAM:${alignr}${offset -416}${memperc}%
${voffset -28}${offset 192}${membar 12,90}
Swap:${alignr}${offset -416}${swapperc}%
${voffset -28}${offset 192}${swapbar 12,90}
${voffset -56}${offset 310}/:${alignr}${offset -100}${fs_used_perc /}%
${alignr}${voffset -28}${fs_bar 12,90 /}
${offset 310}/home:${alignr}${offset -100}${fs_used_perc /home}%
${alignr}${voffset -28}${fs_bar 12,90 /home}

${voffset -16}${color1}PROCESSES ${hr 2}${color}
${voffset 8}
${alignr}${voffset -28}${offset -232}PID
${alignr}${voffset -28}${offset -116}%CPU
${alignr}${voffset -28}${offset -6}%MEM
${top name 1}
${font Inconsolata Medium:size=9}${alignr}${voffset -28}${offset -232}${top pid 1}
${alignr}${voffset -28}${offset -120}${top cpu 1}
${alignr}${voffset -28}${offset -8}${top mem 1}${font}
${top name 2}
${font Inconsolata Medium:size=9}${alignr}${voffset -28}${offset -232}${top pid 2}
${alignr}${voffset -28}${offset -120}${top cpu 2}
${alignr}${voffset -28}${offset -8}${top mem 2}${font}
${top name 3}
${font Inconsolata Medium:size=9}${alignr}${voffset -28}${offset -232}${top pid 3}
${alignr}${voffset -28}${offset -120}${top cpu 3}
${alignr}${voffset -28}${offset -8}${top mem 3}${font}

${voffset -16}${color1}NETWORK ${hr 2}${color}
${lua_parse wireless_image 0 802}
${offset 78}${voffset -24}ESSID:${alignr}${wireless_essid}
${offset 78}${voffset -0}local address:${alignr}${addr wlp58s0}
${offset 78}${voffset 0}${if_up wlp58s0}public address:${alignr}${texeci 3600 wget -q -O /dev/stdout http://checkip.dyndns.org/ | cut -d : -f 2- | cut -d \< -f -1}${endif}
${voffset 4}Down: ${downspeed wlp58s0}${alignr}${offset 0}Up: ${upspeed wlp58s0}
${voffset 3}${downspeedgraph wlp58s0 24,260 AEA79F 6AC612 3840}${alignr}${upspeedgraph wlp58s0 24,260 AEA79F 145D8D 256}${color}
${voffset 3}Total down: ${totaldown wlp58s0}${alignr}Total up: ${totalup wlp58s0}

${voffset -16}${color1}BATTERY ${hr 2}${color}
${lua_parse battery_image 0 1014}
#${image ~/.conky/images/battery.png -p 0,1020}
${voffset -20}${offset 78}${exec head /sys/class/power_supply/BAT0/model_name}
${offset 78}${exec cut -c-4 /sys/class/power_supply/BAT0/charge_full_design} mAh ${exec head /sys/class/power_supply/BAT0/technology}
${voffset -56}${alignr}${exec head /sys/class/power_supply/BAT0/status} ${battery_percent}%
${alignr}${exec acpi -b | awk 'BEGIN { FS = "," } ; { print $NF }'}

${if_match "${wireless_essid}"=="the cake is a lie"}
${voffset -44}${color1}MINECRAFT ${hr 2}${color}
${image ~/.conky/images/server-icon.png -p 0,1132}
${texeci 60 ~/.conky/scripts/status.sh pi 25565 oldworld > ~/.conky/scripts/oldworld_output}
${texeci 60 ~/.conky/scripts/status.sh pi 25566 bigworld > ~/.conky/scripts/bigworld_output}
${offset 78}${voffset -70}Old World (:${color4}25565${color})
${offset 78}${execp awk 'NR==1{print;exit}' ~/.conky/scripts/oldworld_output}
${offset 78}${execp awk 'NR==2{print;exit}' ~/.conky/scripts/oldworld_output}
${offset 78}${execp awk 'NR==3{print;exit}' ~/.conky/scripts/oldworld_output}
${offset 78}${scroll 25 ${execp awk 'NR==4{print;exit}' ~/.conky/scripts/oldworld_output}}
${offset 370}${voffset -140}Big World (:${color4}25566${color})
${offset 370}${execp awk 'NR==1{print;exit}' ~/.conky/scripts/bigworld_output}
${offset 370}${execp awk 'NR==2{print;exit}' ~/.conky/scripts/bigworld_output}
${offset 370}${execp awk 'NR==3{print;exit}' ~/.conky/scripts/bigworld_output}
${offset 370}${scroll 25 ${execp awk 'NR==4{print;exit}' ~/.conky/scripts/bigworld_output}}
${endif}
```


You can't test this script because it calls a boatload of external scripts and images that you won't have, making posting it for you completely pointless. As I said in my second post in this thread. But since you have expressed your extreme skepticism that the behaviour I amply described in the very first post actually happens, good luck to you.

Here is the smaller separate script which doesn't work. You will note that it is functionally identical to the relevant section of the larger script, exactly as I said in the very first post.

```
conky.config = {
background = true,
own_window = true,
own_window_transparent = false,
own_window_type = normal,
own_window_argb_visual = true,
own_window_argb_value = 255,
own_window_hints = 'undecorated,below,sticky,skip_taskbar,skip_pager',
double_buffer = true,
use_spacer = 'none',

use_xft = true,
font = 'Bitstream Vera Sans:size=9',
xftalpha = 1.0,
text_buffer_size = 2048,

format_human_readable = true,
short_units = false,
override_utf8_locale = true,

update_interval = 4,

minimum_height = 5,
minimum_width = 600,

draw_shades = false,

draw_outline = false,
draw_borders = false,
uppercase = false,

border_inner_margin = 0,
border_outer_margin = 0,

border_width = 2,

default_color = 'AEA79F', --Warm Grey 5
color1 = 'DD4814', --Ubuntu Orange
color2 = '95B36A', --Green
color3 = 'C0836B', --Orange
color4 = '748B98', --Blue

alignment = 'top_right',

gap_x = 624,
gap_y = 618,

top_cpu_separate = true,
top_name_width = 30,

cpu_avg_samples = 2,
net_avg_samples = 2,
if_up_strictness = 'link',
}
 
conky.text = [[
${color}
${color1}PROCESSES ${hr 2}${color}
${voffset 8}
${alignr}${voffset -28}${offset -232}PID
${alignr}${voffset -28}${offset -116}%CPU
${alignr}${voffset -28}${offset -6}%MEM
${top name 1}
${font Inconsolata Medium:size=9}${alignr}${voffset -28}${offset -232}${top pid 1}
${alignr}${voffset -28}${offset -120}${top cpu 1}
${alignr}${voffset -28}${offset -8}${top mem 1}${font}
${top name 2}
${font Inconsolata Medium:size=9}${alignr}${voffset -28}${offset -232}${top pid 2}
${alignr}${voffset -28}${offset -120}${top cpu 2}
${alignr}${voffset -28}${offset -8}${top mem 2}${font}
${top name 3}
${font Inconsolata Medium:size=9}${alignr}${voffset -28}${offset -232}${top pid 3}
${alignr}${voffset -28}${offset -120}${top cpu 3}
${alignr}${voffset -28}${offset -8}${top mem 3}${font}
]]
```

And here is the new simple script that you demanded.

```

conky.config = {
own_window = true,
own_window_hints = 'undecorated,below,sticky,skip_taskbar,skip_pager',

use_xft = true,
font = 'Bitstream Vera Sans:size=9',
default_color = 'AEA79F', --Warm Grey 5

alignment = 'top_right',
gap_x = 624,
gap_y = 800,

top_cpu_separate = true,
}
conky.text = [[
Name PID %CPU %MEM
${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
]]
```

You will note that we're on the second page now, and the only posts that discuss the difference in behaviour of the conky top object when top_cpu_separate is toggled are mine.

---

### Post by CantankRus on 2016-08-02
You should really stop killing those cats... it puts you in a bad sarcastic mood.
I'll pass on this one.

---

### Post by CatKiller on 2016-08-02
> **CantankRus said:**
> You should really stop killing those cats... it puts you in a bad sarcastic mood.
I'll pass on this one.

There's a shock.

---

