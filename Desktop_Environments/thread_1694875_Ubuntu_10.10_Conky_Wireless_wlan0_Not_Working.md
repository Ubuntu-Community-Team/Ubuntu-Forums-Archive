---
title: "Ubuntu 10.10 Conky Wireless wlan0 Not Working"
date: 2011-02-25
forum: Desktop Environments
---

### Post by david@iprop on 2011-02-25
Hi there,

Below are my ~/.conkyrc file NETWORK section:

```

{voffset -1}NETWORK ${hr 2}
${if_up wlan0}
${font Poky:size=14}Y${font}${goto 32}${voffset -8}SSID: ${wireless_essid wlan0}
${goto 32}Signal: ${wireless_link_qual wlan0}% ${alignr}${wireless_link_bar 8,60 wlan0}
${voffset 4}${font VariShapes Solid:size=14}q${font}${goto 32}${voffset -6}Up: ${upspeed wlan0}${font} ${alignr}${upspeedgraph wlan0 8,60 F57900 FCAF3E}
${goto 32}Total: ${totalup wlan0}
${voffset 4}${font VariShapes Solid:size=14}Q${font}${goto 32}${voffset -6}Down: ${downspeed wlan0}${font} ${alignr}${downspeedgraph wlan0 8,60 F57900 FCAF3E}
${goto 32}Total: ${totaldown wlan0}
${voffset 4}${font Poky:size=13}w${font}${goto 32}${voffset -8}Local IP: ${alignr}${addr wlan0}
${goto 32}Public IP: ${alignr}${execi 3600 wget -O - http://whatismyip.org/ | tail}
# |--ETH0
${else}${if_up eth0}
${voffset -13}${font VariShapes Solid:size=14}q${font}${goto 32}${voffset -6}Up: ${upspeed eth0}${font} ${alignr}${upspeedgraph eth0 8,60 F57900 FCAF3E}
${goto 32}Total: ${totalup eth0}
${voffset -2}${font VariShapes Solid:size=14}Q${font}${goto 32}${voffset -6}Down: ${downspeed eth0}${font} ${alignr}${downspeedgraph eth0 8,60 F57900 FCAF3E}
${goto 32}Total: ${totaldown eth0}
${voffset -2}${font Poky:size=13}w${font}${goto 32}${voffset -4}Local IP: ${alignr}${addr eth0}
${goto 32}Public IP: ${alignr}${execi 3600 wget -O - http://whatismyip.org/ | tail}
# |--PPP0
${endif}${else}${if_up ppp0}
${voffset -13}${font VariShapes Solid:size=14}q${font}${goto 32}${voffset -6}Up: ${upspeed ppp0}${font} ${alignr}${upspeedgraph ppp0 8,60 F57900 FCAF3E}
${goto 32}Total: ${totalup ppp0}
${voffset -2}${font VariShapes Solid:size=14}Q${font}${goto 32}${voffset -6}Down: ${downspeed ppp0}${font} ${alignr}${downspeedgraph ppp0 8,60 F57900 FCAF3E}
${goto 32}Total: ${totaldown ppp0}
${voffset -2}${font Poky:size=13}w${font}${goto 32}${voffset -4}Local IP: ${alignr}${addr ppp0}
${endif}${else}${voffset 4}${font PizzaDude Bullets:size=12}4${font}${goto 32}Network Unavailable${endif}${endif}
#${voffset -1}WEATHER ${hr 2}

```

Earlier on my wireless is attached as eth1 and it works on to load conky except the Network section is blank. After that I had renamed eth1 to wlan0 and checked at ifconfig it is working fine.

Now the conky won't load and I think something to do with my wlan0.

Need some advise here.

Thanks

---

### Post by david@iprop on 2011-02-25
Apologize, the conky taken quite sometime to take effect. :popcorn:

---

