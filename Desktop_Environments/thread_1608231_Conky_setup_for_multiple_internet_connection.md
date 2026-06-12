---
title: "Conky setup for multiple internet connection ?"
date: 2010-10-28
forum: Desktop Environments
---

### Post by Mobidoy on 2010-10-28
I have my conky setup on wlan0 for my network stats but, I will sometime be using my eth0 or my ttyUSB0 connection, is there a way to tell conky to look for which connection is up and set it properly.

I suspect it will be done with variable and even though I dont know enough Conky syntax and coding, I see it being looking like this: 

```
if {wlan0 is up}
    %network=wlan0
else if {eth0 is up}
    %network=eth0
else if {ttyUSB0 is up}
    %network=ttyUSB0
else
    %network=

```

and in my text area I would have things like

```
${font arial black:size=7}LOCAL: $font${addr **%network**} ${alignr 10} ${color} ${font arial black:size=7}EXTERNAL: $font${execi 14400 wget -O - http://whatismyip.org/ | tail}${color}
```

Anyone can help ?

---

### Post by Mobidoy on 2010-10-29
No one has an idea ?

---

### Post by stinkeye on 2010-10-29
From man conky
```
if_up (interface) 
if INTERFACE exists and is up, display everything between $if_up and the matching $endif
```

${if_up wlan0} blah blah blah ${endif}

eg...look at this post. [**_[COLOR="DarkRed"]http://ubuntuforums.org/showpost.php?p=9834196&postcount=13869[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=9834196&postcount=13869")

The thread title at the top right of that link is a good place to get your conky questions answered.

---

### Post by azertyh on 2010-10-29
hello,

like you, i have 3 ways to connect to internet : wifi, wlan0 and mobile broadband. my conky :

```
${font DejaVu Sans Mono:size=24}&#9850;${font} Internet : ${if_existing /proc/net/route wlan0}WIFI
${font DejaVu Sans Mono:size=24}&#8679;${font} Up : ${upspeedf wlan0}k/s
${upspeedgraph wlan0 24,360 66ffff 6600ff scale -l -t}
${font DejaVu Sans Mono:size=24}&#8681;${font} Down : ${downspeedf wlan0}k/s
${downspeedgraph wlan0 24,360 66ffff 6600ff scale -l -t}${else}${if_existing /proc/net/route eth0}4G
${font DejaVu Sans Mono:size=24}&#8679;${font} Up : ${upspeedf eth0}k/s
${upspeedgraph eth0 24,360 66ffff 6600ff scale -l -t}
${font DejaVu Sans Mono:size=24}&#8681;${font} Down : ${downspeedf eth0}k/s
${downspeedgraph eth0 24,360 66ffff 6600ff scale -l -t}${else}${if_existing /proc/net/route ppp0}3G+
${font DejaVu Sans Mono:size=24}&#8679;${font} Up : ${upspeedf ppp0}k/s
${upspeedgraph ppp0 24,360 66ffff 6600ff scale -l -t}
${font DejaVu Sans Mono:size=24}&#8681;${font} Down : ${downspeedf ppp0}k/s
${downspeedgraph ppp0 24,360 66ffff 6600ff scale -l -t}${else}Non-connecté${endif}${endif}${endif}
```

---

