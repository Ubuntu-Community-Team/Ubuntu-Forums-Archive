---
title: "Conky CPU Temp: command | grep | cut ??"
date: 2011-04-24
forum: Desktop Environments
---

### Post by jonbwilson on 2011-04-24
I got the CPU temp to show up.  Problem is it gives me more info than I need.  Instead of just showing 53°C, it shows "Core 0:      +53.0°C  (high = +100.0°C, crit = +100.0°C)", which is exactly what the output of "sensors" shows.  I know the "cut" command allows you to get rid of that extraneous information, but I don't know the proper syntax.  This is what I've got right now:
```
${goto 6}${voffset 4}${font Devil inside:size=16}1${font}${voffset -4}${goto 32}CPU Temp: ${alignr}${exec sensors | grep 'Core 0'} / ${exec sensors | grep 'Core 1'}
```

Then I know after each 'grep', there would be a | and then cut ??

Just don't know what to put after cut.

Here's the output of sensors:
```
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +56.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +57.0°C  (high = +100.0°C, crit = +100.0°C)  

```

As it is now, it looks pretty out of place.  This is the last piece of the puzzle to get Conky to display all the info I want it to display. Any ideas?

---

### Post by elliotbeken on 2011-04-24
hi there i cant help with the request but i would like to know where i can get a copy of that conky file ?? thanks

---

### Post by mcderb on 2011-04-24
This works on my T9600 Core 2 DUO

${execi 30 sensors | grep 'Core 0' | cut -c15-16}°C
${execi 30 sensors | grep 'Core 1' | cut -c15-16}°C

---

### Post by stinkeye on 2011-04-24
```
${exec sensors | grep 'Core 0' | awk '{print $3}' | cut -c2-3}°C / ${exec sensors | grep 'Core 1' | awk '{print $3}' | cut -c2-3}°C
```
Same as mcderb's but using awk to grab the third grouping before cutting.
In this instance I don't think it matters but is handy to know when you have an output 
that may dip down into single digits and change the cut position.

---

### Post by jonbwilson on 2011-04-24
> **elliotbeken said:**
> hi there i cant help with the request but i would like to know where i can get a copy of that conky file ?? thanks

It's the Conky setup that comes with Pinguy OS, basically.  I'm having to edit the CPU temp portion because the code that was there didn't work for my machine.  You can copy the .conkyrc file from here:

[http://forum.pinguyos.com/Thread-conky-how-to-guide--43]("http://forum.pinguyos.com/Thread-conky-how-to-guide--43")

---

### Post by jonbwilson on 2011-04-24
> **stinkeye said:**
> ```
${exec sensors | grep 'Core 0' | awk '{print $3}' | cut -c2-3}°C / ${exec sensors | grep 'Core 1' | awk '{print $3}' | cut -c2-3}°C
```
Same as mcderb's but using awk to grab the third grouping before cutting.
In this instance I don't think it matters but is handy to know when you have an output 
that may dip down into single digits and change the cut position.

Dude, you're a lifesaver. This works *perfectly.*

If you don't mind, could you explain what that code actually does? I'm trying to learn this stuff and copying and pasting other people's code can only get you so far if you don't know what it means. 

By the way, check the attached screenshot for the finished product.

---

### Post by jonbwilson on 2011-04-24
Actually, maybe you guys can help me with a couple of other sections of the code that I can't get to work.  Namely battery life and fan speed.  I really have no idea how to make those values show up properly.  This is what I have in my conkyrc file for those sections (I know you have to remove the hash):

All this does is show up an empty bar.

```
#${goto 6}${voffset 4}${font StyleBats:size=16}${font}${voffset -4}${goto 32}BATT: ${alignr}${battery_bar 8,60 BAT0}
```

This shows up nothing at all.

```
#${goto 6}${font Martin Vogel's Symbols:size=16}j${font}${voffset -4}${goto 32}Fan Speed: ${alignr}${exec sensors | grep 'RPM'| cut -c16-25}
```

It should be noted that fan speed does not show up when I run the 'sensors' command, so that might not even be something I can display.

---

### Post by wojox on 2011-04-24
This is what I use for my netbook:

```
Fan:$alignr${hwmon 1 fan 1} rpm
Battery:$alignr${battery_percent}%
```

---

### Post by jonbwilson on 2011-04-24
> **wojox said:**
> This is what I use for my netbook:

```
Fan:$alignr${hwmon 1 fan 1} rpm
Battery:$alignr${battery_percent}%
```

Thanks, but the battery percent shows 0, so kind of the same thing as the empty bar. The fan coded you suggested broke conky. :)

---

### Post by stinkeye on 2011-04-24
> **jonbwilson said:**
> Dude, you're a lifesaver. This works *perfectly.*

If you don't mind, could you explain what that code actually does? I'm trying to learn this stuff and copying and pasting other people's code can only get you so far if you don't know what it means. 

By the way, check the attached screenshot for the finished product.

The **grep 'Core 0'** command searches for a pattern matching "Core 0" and prints
the wnole line.
[COLOR="DarkGreen"]**Core 0:      +56.0°C  (high = +100.0°C, crit = +100.0°C)**[/COLOR]  

Then it's piped ("|") to **awk '{print $3}'** which prints the third grouping.
(Continuous characters without a space)

Core 0:      +56.0°C  (high = +100.0°C, crit = +100.0°C)
--1---2---------3-------4--5-----6--------7--8------9
[COLOR="#006400"]**+56.0°C**[/COLOR]

Then piped to the **cut -c2-3** command which cuts from the second to the third character.
[COLOR="#006400"]**56**[/COLOR]

In the terminal run 
```
sensors
```


Then run
```
sensors | grep 'Core 0' | awk '{print $3}' | cut -c2-3
```
and play around with the values.Say use **awk '{print $4}'** instead.

---

### Post by jonbwilson on 2011-04-24
> **stinkeye said:**
> The **grep 'Core 0'** command searches for a pattern matching "Core 0" and prints
the wnole line.
[COLOR="DarkGreen"]**Core 0:      +56.0°C  (high = +100.0°C, crit = +100.0°C)**[/COLOR]  

Then it's piped ("|") to **awk '{print $3}'** which prints the third grouping.
(Continuous characters without a space)

Core 0:      +56.0°C  (high = +100.0°C, crit = +100.0°C)
--1---2---------3-------4--5-----6--------7--8------9
[COLOR="#006400"]**+56.0°C**[/COLOR]

Then piped to the **cut -c2-3** command which cuts from the second to the third character.
[COLOR="#006400"]**56**[/COLOR]

In the terminal run 
```
sensors
```


Then run
```
sensors | grep 'Core 0' | awk '{print $3}' | cut -c2-3
```
and play around with the values.Say use **awk '{print $4}'** instead.

Got it.  Thanks for taking the time to explain that.  It's really helpful.

---

### Post by stinkeye on 2011-04-24
> **jonbwilson said:**
> Got it.  Thanks for taking the time to explain that.  It's really helpful.

It's not that hard to write simple one liners.
I don't write programs or anything.
Just an ex windows user who loves the freedom of Linux.

[**_[COLOR="DarkRed"]http://linux.byexamples.com/[/COLOR]_**]("http://linux.byexamples.com/") is a great site for code snippets or just googling for awk/sed/grep snippets.

The man pages are also helpful although sometimes it's a bit hard to 
understand the syntax for people like me.

---

### Post by jonbwilson on 2011-04-24
I figured out how to show the battery life percentage, but there's a slight hiccup.

If the battery life is less than 100%, it shows up as 99%,

I know where that comma is coming from.  The command I'm using to display it is:

```
${exec acpi | awk '{print $4}'}
```

The output of acpi in the terminal is:

```
Battery 0: Discharging, 99%, discharging at zero rate - will never fully discharge.
```

I've tried adding cut -c5- or cut -c5-14 to the end of it, but that makes it display nothing at all for the battery.

The code I have works fine when the battery is at 100%, but that kind of makes it useless.  Any ideas?

EDIT:  A couple of commands that work when battery is less than 100% are:

```
${exec acpi | grep 'Battery 0' | cut -c22-24}
${exec acpi | awk '{print $4}' | cut -c1-3}
```

But since these are based on exact locations of characters in the output, these won't work when battery life reaches 100% or less than 10%.  There has to be some solution that can show the value (not just characters) and lose the info after it.

---

### Post by stinkeye on 2011-04-24
```
${exec acpi | awk '{print $4}' | tr -d '[=,=]'
```

Deletes any character that matches ","

tr - translate or delete characters.
See man tr.

[COLOR="Gray"]Proudly brought to you by stinkeye's World of Snippets.[/COLOR]

---

### Post by jonbwilson on 2011-04-24
> **stinkeye said:**
> ```
${exec acpi | awk '{print $4}' | tr -d '[=,=]'
```

Deletes any character that matches ","

tr - translate or delete characters.
See man tr.

[COLOR="Gray"]Proudly brought to you by stinkeye's World of Snippets.[/COLOR]

Thanks, that got rid of the comma.  I'm running the battery down to see what it looks like when it hits single digits.  Crossing my fingers.

Thanks for all your help on this.  I'm learning a lot!

---

### Post by stinkeye on 2011-04-24
No problem. I'm off to sleep. 2 am here. :eek:
Check back later.

---

### Post by jonbwilson on 2011-04-24
Worked like a charm.  I wish the battery_bar wasn't empty.  The solution I've found elsewhere says to fix this you have to compile Conky from source.  But that's how I installed it in the first place, so that apparently didn't work for me.

Whatever.  I can live with this for now.  I'll go ahead and mark this as solved.

Thanks for the help everyone!

---

### Post by stinkeye on 2011-04-25
You can use execibar to display battery state as a bar graph.
> **execbar** command 
 Same as exec, except if the first value return is a value between 0-100, it will use that number for a bar. The size for bars can be controlled via the default_bar_size config setting.

**execibar** interval command 
 Same as execbar, except with an interval

```
${execibar 30 acpi | awk '{print $4}' | tr -d '[=,=]'}
```


execibar does not take size arguments so you need to add 
```
default_bar_size [COLOR="Magenta"]x[/COLOR] [COLOR="Magenta"]y[/COLOR]
``` to your config above "TEXT"
to [COLOR="Magenta"]match[/COLOR] your other bars.

---

### Post by jonbwilson on 2011-04-25
> **stinkeye said:**
> You can use execibar to display battery state as a bar graph.


```
${execibar 30 acpi | awk '{print $4}' | tr -d '[=,=]'}
```


execibar does not take size arguments so you need to add 
```
default_bar_size [COLOR="Magenta"]x[/COLOR] [COLOR="Magenta"]y[/COLOR]
``` to your config above "TEXT"
to [COLOR="Magenta"]match[/COLOR] your other bars.

Hey, this worked!  I actually did tried using the "execbar" command once, and it didn't work.  So close.

---

### Post by jonbwilson on 2011-04-25
> **jonbwilson said:**
> Hey, this worked!  I actually did tried using the "execbar" command once, and it didn't work.  So close.

Actually, I take that back.  It worked on the Conky config I was working on at the moment, which is a different one.  I went back to the Conky config I was using in this thread, and for whatever reason it's not taking my default_bar_size 8,60 instruction.  I placed it above TEXT, so I'm really not sure what's going on.  Couldn't find any answers in the "Conky Objects" page online.  So, what could make my default_bar_size argument not work?  For the record, here is my conkyrc file once more:

```
# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Use Xft?
use_xft yes

xftfont Droid Sans:size=8
xftalpha 0.8
text_buffer_size 2048

# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_type override
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 182 0
maximum_width 182

# Draw shades?
draw_shades no
default_color D6D6D6 #4D4D4D
# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 5

# border width
border_width 1

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 25
gap_y 40

# Set default bar size
default_bar_size 8,60

# -- Lua Load -- #
lua_load ~/.draw_bg.lua
lua_draw_hook_pre draw_bg


TEXT
SYSTEM ${hr 2}
${goto 6}${voffset 6}${font OpenLogos:size=22}u${font}${goto 36}${voffset -18}${pre_exec cat /etc/issue.net} $machine
${goto 36}Kernel: ${kernel}
${goto 36}Conky: ${conky_version}
${hr 2}

#CPU
${goto 6}${font StyleBats:size=16}A${font}${voffset -4}${goto 32}CPU1: ${cpu cpu0}% ${alignr}${cpubar cpu0 8,60}
${goto 6}${voffset 4}${font StyleBats:size=16}A${font}${voffset -4}${goto 32}CPU2: ${cpu cpu1}% ${alignr}${cpubar cpu1 8,60}
#${goto 6}${voffset 4}${font StyleBats:size=16}A${font}${voffset -4}${goto 32}CPU3: ${cpu cpu2}% ${alignr}${cpubar cpu2 8,60}
#${goto 6}${voffset 4}${font StyleBats:size=16}A${font}${voffset -4}${goto 32}CPU4: ${cpu cpu3}% ${alignr}${cpubar cpu3 8,60}
#
#RAM
${goto 6}${voffset 4}${font StyleBats:size=16}g${font}${voffset -4}${goto 32}RAM: ${mem} ${alignr}${membar 8,60}
#
#Disk
${goto 6}${voffset 4}${font StyleBats:size=16}x${font}${voffset -4}${goto 32}DISK: ${diskio}${alignr}${diskiograph 8,60 F57900 FCAF3E}
#
#Swap
${goto 6}${voffset 4}${font StyleBats:size=16}j${font}${voffset -4}${goto 32}SWAP: $swapperc% ${alignr}${swapbar 8,60}
#
#Battery
${goto 6}${voffset 4}${font StyleBats:size=16}8${font}${voffset -4}${goto 32}BATT: ${exec acpi | awk '{print $4}' | tr -d '[=,=]'}${alignr}${execibar 30 acpi | awk '{print $4}' | tr -d '[=,=]'}
#
#CPU1 Temp
${goto 6}${voffset 4}${font Devil inside:size=16}1${font}${voffset -4}${goto 32}CPU1 Temp: ${alignr}${exec sensors | grep 'Core 0' | awk '{print $3}' | cut -c2-3}°C
#
#CPU2 Temp
${goto 6}${voffset 4}${font Devil inside:size=16}1${font}${voffset -4}${goto 32}CPU2 Temp: ${alignr}${exec sensors | grep 'Core 1' | awk '{print $3}' | cut -c2-3}°C
#
#Motherboard Temp
#${goto 5}${voffset 4}${font Devil inside:size=16}x${font}${voffset -4}${goto 32}Mother Temp: ${alignr}${exec sensors | grep 'MB Temperature' | cut -c19-20}°C / ${color #FCAF3E}${exec sensors | grep 'MB Temperature' | cut -c37-38}°C$color
#
#HD Temp
${goto 4.5}${voffset 2}${font Poky:size=15}y${font}${voffset -6}${goto 32}HD Temp:${alignr}${exec hddtemp /dev/sda -n --unit=C}°C
#
#Fan Speed
#${goto 6}${font Martin Vogel's Symbols:size=16}j${font}${voffset -4}${goto 32}Fan Speed: ${alignr}${exec sensors | grep 'RPM'| cut -c16-25}
#
#Uptime
${goto 6}${voffset 4}${font StyleBats:size=16}q${font}${voffset -4}${goto 32}Uptime: ${alignr}${uptime}
#
#Processes Running
${goto 6}${voffset 4}${font StyleBats:size=16}k${font}${voffset -4}${goto 32}Processes: ${alignr}$processes ($running_processes running)
#
#Top 4 Processes
${goto 7.5}${voffset 4}${font Poky:size=15}a${font}${goto 32}${voffset -10}Highest: ${alignr 13}CPU${alignr}RAM
${goto 32}${voffset -5.5}${hr 1}
${voffset -1}${goto 32}${top name 1} ${goto 124}${top cpu 1}${alignr }${top mem 1}
${voffset -1}${goto 32}${top name 2} ${goto 124}${top cpu 2}${alignr }${top mem 2}
${voffset -1}${goto 32}${top name 3} ${goto 124}${top cpu 3}${alignr }${top mem 3}
${voffset -1}${goto 32}${top name 4} ${goto 124}${top cpu 4}${alignr }${top mem 4}

${voffset -1}DATE ${hr 2}
${alignc 35}${font Arial Black:size=26}${time %H:%M }${font}
${alignc}${time %A %d %B}

${voffset -1}HD ${hr 2}
${goto 3}${voffset 4}${font Poky:size=16}H${font}${goto 29}${voffset -11} Root: ${fs_used_perc /}%${alignr}${fs_size /}
${goto 29} Free: ${fs_free /}${alignr}${fs_bar 8,60 /}
#${goto 3}${voffset 8}${font Poky:size=16}H${font}${goto 29}${voffset -11} Home: ${fs_used_perc /home}%${alignr}${fs_size /home}
#${goto 29} Free: ${fs_free /home}${alignr}${fs_bar 8,60 /home}

${voffset -1}NETWORK ${hr 2}
${if_up wlan0}
${font Poky:size=14}Y${font}${goto 32}${voffset -8}SSID: ${wireless_essid wlan0}
${goto 32}Signal: ${wireless_link_qual wlan0}% ${alignr}${wireless_link_bar 8,60 wlan0}
${voffset 4}${font VariShapes Solid:size=14}q${font}${goto 32}${voffset -6}Up: ${upspeed wlan0}${font} ${alignr}${upspeedgraph wlan0 8,60 F57900 FCAF3E}
${goto 32}Total: ${totalup wlan0}
${voffset 4}${font VariShapes Solid:size=14}Q${font}${goto 32}${voffset -6}Down: ${downspeed wlan0}${font} ${alignr}${downspeedgraph wlan0 8,60 F57900 FCAF3E}
${goto 32}Total: ${totaldown wlan0}
${voffset 4}${font Poky:size=13}w${font}${goto 32}${voffset -8}Local IP: ${alignr}${addr wlan0}
${goto 32}Public IP: ${alignr}${execi 3600 wget -O - http://www.whatismyip.com/automation/n09230945.asp | tail}
# |--ETH0
${else}${if_up eth0}
${voffset -13}${font VariShapes Solid:size=14}q${font}${goto 32}${voffset -6}Up: ${upspeed eth0}${font} ${alignr}${upspeedgraph eth0 8,60 F57900 FCAF3E}
${goto 32}Total: ${totalup eth0}
${voffset -2}${font VariShapes Solid:size=14}Q${font}${goto 32}${voffset -6}Down: ${downspeed eth0}${font} ${alignr}${downspeedgraph eth0 8,60 F57900 FCAF3E}
${goto 32}Total: ${totaldown eth0}
${voffset -2}${font Poky:size=13}w${font}${goto 32}${voffset -4}Local IP: ${alignr}${addr eth0}
${goto 32}Public IP: ${alignr}${execi 3600 wget -O - http://www.whatismyip.com/automation/n09230945.asp | tail}
# |--PPP0
${endif}${else}${if_up ppp0}
${voffset -13}${font VariShapes Solid:size=14}q${font}${goto 32}${voffset -6}Up: ${upspeed ppp0}${font} ${alignr}${upspeedgraph ppp0 8,60 F57900 FCAF3E}
${goto 32}Total: ${totalup ppp0}
${voffset -2}${font VariShapes Solid:size=14}Q${font}${goto 32}${voffset -6}Down: ${downspeed ppp0}${font} ${alignr}${downspeedgraph ppp0 8,60 F57900 FCAF3E}
${goto 32}Total: ${totaldown ppp0}
${voffset -2}${font Poky:size=13}w${font}${goto 32}${voffset -4}Local IP: ${alignr}${addr ppp0}
${endif}${else}${voffset 4}${font PizzaDude Bullets:size=12}4${font}${goto 32}Network Unavailable${endif}${endif}
#
#${voffset -1}WEATHER ${hr 2}
#
#${voffset -10}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 conkyForecast --location=USTX0057 --datatype=WF --imperial}${font}
#${voffset -50}${font Weather:size=40}y${font}  ${voffset -38}${font Arial Black:size=26}${execi 600 conkyForecast --location=USTX0057 --datatype=HT --imperial}${font}
#
#${alignc 43}${execpi 600 conkyForecast --location=USTX0057 --datatype=DW --imperial --startday=1 --shortweekday} ${alignc 8}${execpi 600 conkyForecast --location=USTX0057 --datatype=DW --imperial --startday=2 --shortweekday} #${alignc -29}${execpi 600 conkyForecast --location=USTX0057 --datatype=DW --imperial --startday=3 --shortweekday} ${alignc -64}${execpi 600 conkyForecast --location=USTX0057 --datatype=DW --imperial --startday=4 --shortweekday}
#${alignc 75}${font ConkyWeather:size=28}${execpi 600 conkyForecast --location=USTX0057 --datatype=WF --imperial --startday=1 --endday=4 --spaces=1}${font}
#${font DejaVu Sans:size=7}${alignc 48}${execpi 600 conkyForecast --location=USTX0057 --datatype=HT --imperial --startday=1 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=USTX0057 --datatype=LT --imperial --startday=1 --hideunits --centeredwidth=3} ${alignc -14}${execpi 600 conkyForecast --location=USTX0057 --datatype=HT --imperial --startday=2 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=USTX0057 --datatype=LT --imperial --startday=2 --hideunits --centeredwidth=3} ${alignc -40}${execpi 600 conkyForecast --location=USTX0057 --datatype=HT --imperial --startday=3 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=USTX0057 --datatype=LT --imperial --startday=3 --hideunits --centeredwidth=3} ${alignr 6}${execpi 600 conkyForecast --location=USTX0057 --datatype=HT --imperial --startday=4 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=USTX0057 --datatype=LT --imperial --startday=4 --hideunits --centeredwidth=3}${font}
#${voffset 4}Location:${alignr}${execi 600 conkyForecast --location=USTX0057 --datatype=CN}
#Last Updated: ${alignr} ${execi 600 conkyForecast --location=USTX0057 --hideunits --datatype=LU -m 0 }
#Feels Like:${alignr}${execi 600 conkyForecast --location=USTX0057 --datatype=LT --imperial}
#Dew Point: ${alignr}${execi 600 conkyForecast --location=USTX0057 --datatype=DP --imperial}
#Current Condition:${alignr}${execi 600 conkyForecast --location=USTX0057 --datatype=CC}
#Chance of Precip: ${alignr}${execi 600 conkyForecast  --location=USTX0057 --startday=0 --datatype=PC}
#Humidity: ${alignr}${execi 600 conkyForecast --location=USTX0057 --datatype=HM}
#Wind: ${alignr}${execi 600 conkyForecast --location=USTX0057 --datatype=WS --imperial} - ${execi 600 conkyForecast --location=USTX0057 --datatype=WD}
#Pressure: ${alignr}${execi 600 conkyForecast --location=USTX0057 --hideunits --datatype=BR}
#Visibility: ${alignr}${execi 600 conkyForecast --location=USTX0057 --datatype=VI --imperial}
#Sunrise: ${alignr}${execi 600 conkyForecast --location=USTX0057 --datatype=SR}
#Sunset: ${alignr}${execi 600 conkyForecast --location=USTX0057 --datatype=SS}
#Moon Phase:${alignr 8}${execi 600 conkyForecast --location=USTX0057 --datatype=MP} ${font MoonPhases:size=8}${execi 600 conkyForecast --location=USTX0057 --datatype=MF}${font}
${hr 2}
```

---

### Post by jonbwilson on 2011-04-25
Nevermind, I figured it out.  Oddly enough, the size values in the default_bar_size are opposite from those that I put as arguments on the other bars.  So, I put 8,60 for those bars and they came out the right size.  But for default_bar_size, I had to put 60 8 (without the comma).

Everything looks good now. :)

---

### Post by kumaraasheesh on 2011-11-27
# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Use Xft?
use_xft yes

xftfont Droid Sans:size=8
xftalpha 0.8
text_buffer_size 2048

# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_type override
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 182 0
maximum_width 182

# Draw shades?
draw_shades no
default_color #FFFFFF
# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 5

# border width
border_width 1

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 25
gap_y 20

# -- Lua Load -- #
lua_load ~/.draw_bg.lua
lua_draw_hook_pre draw_bg
TEXT
## Uncomment for hard-coded ID (static)
${voffset -33}${font OpenLogos:size=105}${color #FFFFFF}v${font}${voffset -76}${goto 179}${font UbuntuTitleBold:size=19.8}${color #FFFFFF}1${offset 3}1${offset 1}.${offset 1}1${offset 1}0${font}
####
## Additional ID (branch version, code name, release date, etc.)
${voffset -2}${goto 184}${font Ubuntu-B:size=8.5}${color #FFFFFF}
${goto 36}Kernel: ${kernel}  

${voffset -1}CALENDER
${hr 2}
## Uncomment for Conky 1.8.1 (use mono fonts only)
${voffset -10}${offset 10}${font DroidSansMono:size=10}
${color #FFFFFF}${execpi 60 
VinDSL_Cal_12=`date +%-d`; cal -h | sed -e 's/\r//g' -e 's/^/ /g' -e '1d' -e 's/\<'"$VinDSL_Cal_12"'\>/${color #FFFFFF}&${color #FFFFFF}/'}
${font Times New Roman:style=Bold:pixelsize=44}${color #FFFFFF}${alignc}${time %H:%M:%S} ${font Times New Roman:style=Bold:pixelsize=18}
${alignc}${time %A} 
${alignc}${time %B %e} ${time %Y}
${hr 2}
${voffset 1}SYSTEM
${goto 6}${font StyleBats:size=12}A${font}${voffset -4}${goto 32}CPU1: ${cpu cpu0}% ${alignr}${cpubar cpu0 8,60}
${goto 6}${voffset 4}${font StyleBats:size=16}A${font}${voffset -4}${goto 32}CPU2: ${cpu cpu1}% ${alignr}${cpubar cpu1 8,60}
#${goto 6}${voffset 4}${font StyleBats:size=16}A${font}${voffset -4}${goto 32}CPU3: ${cpu cpu2}% ${alignr}${cpubar cpu2 8,60}
#${goto 6}${voffset 4}${font StyleBats:size=16}A${font}${voffset -4}${goto 32}CPU4: ${cpu cpu3}% ${alignr}${cpubar cpu3 8,60}
${goto 6}${voffset 4}${font StyleBats:size=16}g${font}${voffset -4}${goto 32}RAM: ${mem} ${alignr}${membar 8,60}
${goto 6}${voffset 4}${font StyleBats:size=16}x${font}${voffset -4}${goto 32}DISK: ${diskio}${alignr}${diskiograph 8,60 F57900 FCAF3E}
${goto 6}${voffset 4}${font StyleBats:size=16}j${font}${voffset -4}${goto 32}SWAP: $swapperc% ${alignr}${swapbar 8,60}
${goto 6}${voffset 4}${font Devil inside:size=16}1${font}${voffset -4}${goto 32}CPU Temp: ${alignr}${exec sensors | grep 'CPU Temperature' | cut -c19-20}°C / ${color #FFFFFF}${exec sensors | grep 'CPU Temperature' | cut -c37-38}°C$color
${goto 5}${voffset 4}${font Devil inside:size=16}x${font}${voffset -4}${goto 32}Mother Temp: ${alignr}${exec sensors | grep 'MB Temperature' | cut -c19-20}°C / ${color #FFFFFF}${exec sensors | grep 'MB Temperature' | cut -c37-38}°C$color
${goto 4.5}${voffset 2}${font Poky:size=15}y${font}${voffset -6}${goto 32}HD Temp:${alignr}${exec hddtemp /dev/sda -n --unit=C}°C / ${color #FFFFFF}${exec sensors | grep 'CPU Temperature' | cut -c54-55}°C$color
${goto 6}${font Martin Vogel's Symbols:size=16}j${font}${voffset -4}${goto 32}Fan Speed: ${alignr}${exec sensors | grep 'RPM'| cut -c16-25}
${goto 6}${voffset 4}${font StyleBats:size=16}q${font}${voffset -4}${goto 32}Uptime: ${alignr}${uptime}
${goto 6}${voffset 4}${font StyleBats:size=16}k${font}${voffset -4}${goto 32}Processes: ${alignr}$processes ($running_processes running)
${goto 7.5}${voffset 4}${font Poky:size=15}a${font}${goto 32}${voffset -10}Highest: ${alignr 13}CPU${alignr}RAM
${hr 2}
${voffset -1}${goto 32}${top name 1} ${goto 124}${top cpu 1}${alignr }${top mem 1}
${voffset -1}${goto 32}${top name 2} ${goto 124}${top cpu 2}${alignr }${top mem 2}
${voffset -1}${goto 32}${top name 3} ${goto 124}${top cpu 3}${alignr }${top mem 3}
${voffset -1}${goto 32}${top name 4} ${goto 124}${top cpu 4}${alignr }${top mem 4}
${voffset -1}HD
${goto 3}${voffset 4}${font Poky:size=16}H${font}${goto 29}${voffset -11} Root: ${fs_used_perc /}%${alignr}${fs_size /}
${goto 29} Free: ${fs_free /}${alignr}${fs_bar 8,60 /}
#${goto 3}${voffset 8}${font Poky:size=16}H${font}${goto 29}${voffset -11} Home: ${fs_used_perc /home}%${alignr}${fs_size /home}
#${goto 29} Free: ${fs_free /home}${alignr}${fs_bar 8,60 /home}

${voffset -1}NETWORK
${if_up wlan0}
${font Poky:size=14}Y${font}${goto 32}${voffset -8}SSID: ${wireless_essid wlan0}
${goto 32}Signal: ${wireless_link_qual wlan0}% ${alignr}${wireless_link_bar 8,60 wlan0}
${voffset 4}${font VariShapes Solid:size=14}q${font}${goto 32}${voffset -6}Up: ${upspeed wlan0}${font} ${alignr}${upspeedgraph wlan0 8,60 F57900 FCAF3E}
${goto 32}Total: ${totalup wlan0}
${voffset 4}${font VariShapes Solid:size=14}Q${font}${goto 32}${voffset -6}Down: ${downspeed wlan0}${font} ${alignr}${downspeedgraph wlan0 8,60 F57900 FCAF3E}
${goto 32}Total: ${totaldown wlan0}
${voffset 4}${font Poky:size=13}w${font}${goto 32}${voffset -8}Local IP: ${alignr}${addr wlan0}
${goto 32}Public IP: ${alignr}${execi 3600 wget -O - [http://automation.whatismyip.com/n09230945.asp](http://automation.whatismyip.com/n09230945.asp) | tail}
# |--ETH0
${else}${if_up eth0}
${voffset -13}${font VariShapes Solid:size=14}q${font}${goto 32}${voffset -6}Up: ${upspeed eth0}${font} ${alignr}${upspeedgraph eth0 8,60 F57900 FCAF3E}
${goto 32}Total: ${totalup eth0}
${voffset -2}${font VariShapes Solid:size=14}Q${font}${goto 32}${voffset -6}Down: ${downspeed eth0}${font} ${alignr}${downspeedgraph eth0 8,60 F57900 FCAF3E}
${goto 32}Total: ${totaldown eth0}
${voffset -2}${font Poky:size=13}w${font}${goto 32}${voffset -4}Local IP: ${alignr}${addr eth0}
${goto 32}Public IP: ${alignr}${execi 3600 wget -O - [http://automation.whatismyip.com/n09230945.asp](http://automation.whatismyip.com/n09230945.asp) | tail}
# |--PPP0
${endif}${else}${if_up ppp0}
${voffset -13}${font VariShapes Solid:size=14}q${font}${goto 32}${voffset -6}Up: ${upspeed ppp0}${font} ${alignr}${upspeedgraph ppp0 8,60 F57900 FCAF3E}
${goto 32}Total: ${totalup ppp0}
${voffset -2}${font VariShapes Solid:size=14}Q${font}${goto 32}${voffset -6}Down: ${downspeed ppp0}${font} ${alignr}${downspeedgraph ppp0 8,60 F57900 FCAF3E}
${goto 32}Total: ${totaldown ppp0}
${voffset -2}${font Poky:size=13}w${font}${goto 32}${voffset -4}Local IP: ${alignr}${addr ppp0}
${endif}${else}${voffset 4}${font PizzaDude Bullets:size=12}4${font}${goto 32}Network Unavailable${endif}${endif}



This is my conkyrc file. It is not showing CPU temp, HDD temp ect correctly. What has gone wrong? Can anyone help plz?

---

### Post by kumaraasheesh on 2011-11-27
All the temperature related things are not show properly. Screenshot attached. 
Other things are displayed correctly in the conky. If there are certain things which are useless in the file that may also be deleted. Can someone Plz help.

---

### Post by stinkeye on 2011-11-27
> **kumaraasheesh said:**
> All the temperature related things are not show properly. Screenshot attached. 
Other things are displayed correctly in the conky. If there are certain things which are useless in the file that may also be deleted. Can someone Plz help.
**[COLOR="Red"]Edit[/COLOR] Just seen your previous post with config.**
For help you would need to post your conky config.

Also the outputs of the terminal commands would help.
When posting please post between the code blocks.
Paste in each output then highlight with right mouse and hit the code button "#" to enclose in code blocks.
```
sensors
```
and
```
hddtemp /dev/sd[COLOR="Red"]x[/COLOR]
```
Where [COLOR="red"]x[/COLOR] is your drive. eg **/dev/sd[COLOR="Red"]a[/COLOR]**

Have you installed **lm-sensors** and **hddtemp**?

---

### Post by dolmance41 on 2011-11-27
this is NOT solved!!! i have tried EVERYTHING and NOTHING works!!! here is my output from sensors....PLEASE someone tell me the line i need to show my cpu temp in conky!!!!! acpitz-virtual-0 Adapter: Virtual device temp1:         +0.0°C  (crit = +105.0°C)  k10temp-pci-00c3 Adapter: PCI adapter temp1:        +65.5°C  (high = +70.0°C)  i have no idea how to format this but i have been trying for 5 days now with NO results!!! please help!!! [email]dolmance41@yahoo.com[/email]

---

### Post by stinkeye on 2011-11-27
> **dolmance41 said:**
> this is NOT solved!!! i have tried EVERYTHING and NOTHING works!!! here is my output from sensors....PLEASE someone tell me the line i need to show my cpu temp in conky!!!!! acpitz-virtual-0 Adapter: Virtual device temp1:         +0.0°C  (crit = +105.0°C)  k10temp-pci-00c3 Adapter: PCI adapter temp1:        +65.5°C  (high = +70.0°C)  i have no idea how to format this but i have been trying for 5 days now with NO results!!! please help!!! [email]dolmance41@yahoo.com[/email]
Well, if you copy and paste the way it appears in the terminal I can help.
eg
```
glen@Oneiric:~$ sensors
it8720-isa-0228
Adapter: ISA adapter
in0:          +1.06 V  (min =  +0.00 V, max =  +4.08 V)
in1:          +1.92 V  (min =  +0.00 V, max =  +4.08 V)
in2:          +3.38 V  (min =  +0.00 V, max =  +4.08 V)
+5V:          +2.99 V  (min =  +0.00 V, max =  +4.08 V)
in4:          +3.10 V  (min =  +0.00 V, max =  +4.08 V)
in5:          +1.07 V  (min =  +0.00 V, max =  +4.08 V)
in6:          +3.38 V  (min =  +0.00 V, max =  +4.08 V)
5VSB:         +3.02 V  (min =  +0.00 V, max =  +4.08 V)
Vbat:         +3.22 V  
fan1:        1973 RPM  (min =    0 RPM)
fan2:           0 RPM  (min =    0 RPM)
fan3:           0 RPM  (min =    0 RPM)
fan5:           0 RPM  (min =    0 RPM)
temp1:        +39.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:        +39.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
temp3:        +80.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
cpu0_vid:    +1.250 V

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +35.2°C  (high = +70.0°C)
                       (crit = +72.0°C, hyst = +70.0°C)
```
> this is NOT solved!!! i have tried EVERYTHING and NOTHING works!!!
PS This is someone elses thread and it was solved for them.

---

### Post by kumaraasheesh on 2011-12-02
> **stinkeye said:**
> **[COLOR=Red]Edit[/COLOR] Just seen your previous post with config.**
For help you would need to post your conky config.

Also the outputs of the terminal commands would help.
When posting please post between the code blocks.
Paste in each output then highlight with right mouse and hit the code button "#" to enclose in code blocks.
```
sensors
```and
```
hddtemp /dev/sd[COLOR=Red]x[/COLOR]
```Where [COLOR=red]x[/COLOR] is your drive. eg **/dev/sd[COLOR=Red]a[/COLOR]**

Have you installed **lm-sensors** and **hddtemp**?



This is what I got when I typed 'sensors' in terminal.
ashish@ashish-System-Product-Name:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +49.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:       +46.0°C  (high = +86.0°C, crit = +100.0°C)

w83627dhg-isa-0290
Adapter: ISA adapter
Vcore:        +1.23 V  (min =  +0.00 V, max =  +1.74 V)
in1:          +1.90 V  (min =  +0.26 V, max =  +0.71 V)  ALARM
AVCC:         +3.42 V  (min =  +2.98 V, max =  +3.63 V)
+3.3V:        +3.42 V  (min =  +2.98 V, max =  +3.63 V)
in4:          +1.12 V  (min =  +0.22 V, max =  +1.41 V)
in5:          +1.61 V  (min =  +1.71 V, max =  +0.62 V)  ALARM
in6:          +0.93 V  (min =  +0.42 V, max =  +0.68 V)  ALARM
3VSB:         +3.44 V  (min =  +2.98 V, max =  +3.63 V)
Vbat:         +3.34 V  (min =  +2.70 V, max =  +3.30 V)  ALARM
fan1:           0 RPM  (min =   46 RPM, div = 128)  ALARM
fan2:        1250 RPM  (min = 3668 RPM, div = 8)  ALARM
fan3:           0 RPM  (min = 5273 RPM, div = 8)  ALARM
fan4:           0 RPM  (min = 112500 RPM, div = 4)  ALARM
fan5:           0 RPM  (min = 5921 RPM, div = 4)  ALARM
temp1:        +25.0°C  (high = +35.0°C, hyst = +99.0°C)  sensor = thermistor
temp2:        +14.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode

And this is my disk details

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    62916607    31457280   83  Linux
/dev/sdb2        62918654   312580095   124830721    5  Extended
/dev/sdb5        62918656    68161535     2621440   82  Linux swap / Solaris
/dev/sdb6        68163584   312580095   122208256   83  Linux


And sorry for replying late as I was preoccupied with other things.

---

### Post by stinkeye on 2011-12-02
Which temp reading do you want.
Best way is to reboot and look in your bios for cpu temp and 
choose the one in the sensors output which is closest.

Try this in terminal for the "Core 0" temp...
```
sensors | grep "Core 0" | awk '{print $3}' | cut -c2-3
```


If that works the conky line would be 
```
${execpi [COLOR="Magenta"]3[/COLOR] sensors | grep "Core 0" | awk '{print $3}' | cut -c2-3}
```
Where [COLOR="magenta"]3[/COLOR] is how often to check in secs.

---

