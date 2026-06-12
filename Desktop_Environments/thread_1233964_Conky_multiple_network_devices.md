---
title: "Conky multiple network devices"
date: 2009-08-07
forum: Desktop Environments
---

### Post by acrocephalus on 2009-08-07
Hello,
I have started configurating my conky widget. I use both wired and wirless network connections, and I would like to know how to make Conky to detect which connection I use. This is my .conkyrc network section
```
${color lightgrey}Networking:
 Down:${color #8844ee} ${downspeed wlan0} k/s${color lightgrey} ${offset 70}Up:${color #22ccff} ${upspeed wlan0} k/s
${color black}${downspeedgraph wlan0 32,150 ff0000 0000ff} $alignr${color black}${upspeedgraph wlan0 32,150 0000ff ff0000}
```
Any idea?
Best,

Dani

---

### Post by Phobiac on 2009-08-07
Try this
```
${if_existing /proc/net/route wlan0}
codeyouwantconkytodo
${else}${if_existing /proc/net/route eth0}
codeyouwantconkytodo
{endif}
```
If you have more and/or different network devices, just add an else section or edit the name. I took this code from the conky-colors script, which is really great for setting up conky. It's here if you want to take a look.
[http://www.gnome-look.org/content/show.php/CONKY-colors?content=92328](http://www.gnome-look.org/content/show.php/CONKY-colors?content=92328)

---

