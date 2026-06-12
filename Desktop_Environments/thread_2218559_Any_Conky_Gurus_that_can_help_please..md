---
title: "Any Conky Gurus that can help please."
date: 2014-04-21
forum: Desktop Environments
---

### Post by The-Valk on 2014-04-21
I have a conky script that I have used for quite a few years.
The OS I have been using for a while was Mint 16 but I thought I would give Ubuntu 1404 a try as it is LTS.
Most of the script works fine but one area fails and I cannot get any help by Googling.
Here is the code in question.
```
${alignc}Local IP (${addr eth0})
${voffset 12}Down: ${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${color2}${downspeedgraph eth0 20,130 ff0000 0000ff} ${alignr}${upspeedgraph eth0 20,130 0000ff ff0000}${color orange}
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
${voffset 16}Nameservers:${offset 8}${nameserver 1}${alignr}${nameserver 2}
```
The local IP is correct so eth0 is the correct interface.
I get 0B for all other values and the nameserver is shown as 127.0.1.1

Any help on adjusting the Conky Code for the new Ubuntu would be great.

---

