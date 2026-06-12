---
title: "Conky ro monitor network"
date: 2010-07-31
forum: Desktop Environments
---

### Post by acrocephalus on 2010-07-31
Hello!
I have set up a conky script to monitor my network connection. This is my code:
```
${if_up wlan0}${color orange}WIRELESS NETWORK${hr 2}$color
Wireless ESSID: ${wireless_essid wlan0} Address: ${addr wlan0}
Bitrate: ${wireless_bitrate wlan0}
Signal: ${wireless_link_qual_perc wlan0}% ${wireless_link_bar wlan0}
Down: $color${downspeed wlan0} k/s ${alignr}Up: ${upspeed wlan0} k/s
${downspeedgraph wlan0 25,140 000000} ${alignr}${upspeedgraph wlan0 
25,140 000000}$color
Total: ${totaldown wlan0} ${alignr}Total: ${totalup wlan0}${endif}
${if_up eth0}${color orange}WIRED NETWORK${hr 2}$color
Address: ${addr eth0}
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000} ${alignr}${upspeedgraph eth0 
25,140 000000}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}${endif}
```
The problem is that both connections (wireless and wired) show in screen even if I am using only one of them. For example, I can see the wired section if I am using the wireless connection (showing no data, of course). How can I set up the script so that only shows the data corresponding to the used connection? 
Cheers!

Dani

---

### Post by stinkeye on 2010-07-31
I think you may need some ${else} statements in there.
eg
${if_up wlan0} what you want to show if wireless up ${else}

You will get a quicker and more knowledgeable  answer here from the conkyholics.
[**_[COLOR="DarkRed"]Post your .conkyrc files w/ screenshots[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=281865")

---

### Post by acrocephalus on 2010-07-31
Great! Now it works.
Thank you so much!!

Dani

---

