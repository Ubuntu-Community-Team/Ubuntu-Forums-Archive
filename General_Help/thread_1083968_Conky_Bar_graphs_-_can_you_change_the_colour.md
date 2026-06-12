---
title: "Conky Bar graphs - can you change the colour?"
date: 2009-03-01
forum: General Help
---

### Post by 5BallJuggler on 2009-03-01
I would like to change the colour of the Bat bargraph, currently it is light blue, I would like to make the left side Red indicating low battery and the right side Green indicating a charged battery, here is my conkyrc

Is there anyone who can help?

```
TEXT
${color #0077ff}${font Bitstream Vera Sans Mono:size=12}${alignc}$sysname $kernel ${alignr}
${offset 50}${font Bitstream Vera Sans Mono:size=12}${alignc}${time}

${offset 66}${font ConkyWeather:style=Bold:size=40}${execi 1800 conkyForecast --location=UKXX0017 --datatype=WF}   ${font ConkyWindNESW:size=40}${execi 1800 conkyForecast --location=UKXX0017 --datatype=BS}  ${font Moon Phases:size=34}${execi 1800 conkyForecast --location=UKXX0017 --datatype=MF}${font}
${offset 66}${execi 1800 conkyForecast --location=UKXX0017 --datatype=HT --centeredwidth=4}/${execi 1800 conkyForecast --location=UKXX0017 --datatype=LT --centeredwidth=4}     ${execi 1800 conkyForecast --location=UKXX0017 --datatype=WS --imperial} - ${execi 1800 conkyForecast --location=UKXX0017 --datatype=WD}      Moon
${hr}
${alignr}${color #0077ff}Uptime:$color $uptime ${color #0077ff} Load:$color $loadavg
${color #0077ff}CPU ${alignr}${color #00ff00}${cpugraph 0 30,255 104E8B 00ff00} 
${color #0077ff}Disk I/O ${alignr}${color #00ff00}${diskiograph 30,255 104E8B 00ff00 750}
${color #0077ff}RAM Usage:$color $mem${color #0077ff}/${color}$memmax - $memperc% 
${color #0077ff}Swap Usage:$color $swap${color #0077ff}/${color}$swapmax - $swapperc%  
${color #0077ff}Mem usage ${alignr}${memgraph 30,255 104E8B 00ff00} 
${color #0077ff}Bat **${alignr}${battery_bar 6,255 BAT1}**
${color #00ff00}Net Down:
${color #00ff00}   ${downspeed wlan0} k/s ${alignr}${color #00ff00}${downspeedgraph wlan0 30,255 104E8B 00ff00} 
${color #ff0000}Net Up:
${color #ff0000}   ${upspeed wlan0} k/s ${alignr}${color #ff0000}${upspeedgraph wlan0 30,255 104E8B ff0000}
${color #0077ff}${hr}
${color #0077ff}Top Processes:
${color #0077ff}Name              PID     CPU%   MEM%
${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color #0077ff}Mem usage
${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}
```

i've tried using this format for the bar but it does not work:- **${memgraph 30,255 104E8B 00ff00}**

---

### Post by cullam on 2009-06-01
As i have been banging my head against the wall trying the same.. i am <<<BUMPING>>> this thread hoping there are any conky gurus that may offer any help on this issue.

;)

---

### Post by Lendo on 2011-03-21
I've been trying to do the same thing with CPU1-8 bars, to start blue and turn red with higher load, but have not found answer anywhere.

---

### Post by Sector11 on 2011-03-25
"bars" don't do that - "graphs" do.

However there is no "bargraph" so NO!

However there is GOOD news.... LUA.

talk to mrpeachy or wlourf on the mega conky thread.

They both have LUA scripts that can do what you want!

---

