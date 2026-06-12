---
title: "Conky on top of applications at startup"
date: 2009-02-11
forum: General Help
---

### Post by Dooley on 2009-02-11
Hey all,

Just wonder if anyone came across the same problem.
When I add conky to auto-start with gnome via sessions, conky is display above all applications. However when I kill conky and restart it, it works fine and as it should.

Is there a way to solve this?

---

### Post by mattman on 2009-02-11
You should start Conky with a script and add the script to start with the session.

```
#!/bin/bash
sleep 20 &&
conky -c ~/.conkyrc &
```

If 20 isn't long enough try 30.

---

### Post by Dooley on 2009-02-13
Thanks,

30 seconds worked fine. Just another quick one. I can't see the desktop icons behind conky, is there a way to solve this?

---

### Post by binbash on 2009-02-13
> **mattman said:**
> You should start Conky with a script and add the script to start with the session.

```
#!/bin/bash
sleep 20 &&
conky -c ~/.conkyrc &
```

If 20 isn't long enough try 30.

Thanks my problem is fixed also  :)

---

### Post by m_duck on 2009-02-13
> **Dooley said:**
> I can't see the desktop icons behind conky, is there a way to solve this?Because conky uses fake transparency (it looks at the root wallpaper and just draws that as a background to itself - I think) there is not a way to see icons behind it. You could change the position of your conky so that it won't get in the way of icons.

---

### Post by ben2talk on 2009-02-13
> **m_duck said:**
> Because conky uses fake transparency (it looks at the root wallpaper and just draws that as a background to itself - I think) there is not a way to see icons behind it. You could change the position of your conky so that it won't get in the way of icons.

Setting up conky, have a few shorcuts on desktop to make life simple - a 'conky editor' set to open the config file in gedit, then a 'kill conky' which I place halfway under the conky window - killall conky (give it a nice skull icon :P) and then the conky editor.

The transparency is fake - that's annoying, so make it cool and black.

Use the 'kill conky' icon on your desktop to either kill conky (revealing icons hidden beneath, including the 'conky' startup icon you can click to fire it up again)

I use a folder now instead of my desktop - with Super+D I get Desktop in Nautilus - no problem seeing it all there, and no need to bother minimising windows!

Try 'magneto' font for headers in conky, looks great ;)

Try stuff like:

$stippled_hr 2##################################################
${color 006699}${cpugraph 2F4F4F CD5C5C}${color green}
${font Verdana:bold:size=12}${downspeed wlan0}kb/s ${alignr}${color orange}${upspeed wlan0}kb/s${font }
${color green}${downspeedgraph wlan0 50,120 008000 00FF00} ${color orange}${upspeedgraph wlan0 50, 75 000000 DDA0DD} ${font Verdana:bold:size=6} ${color green}
${COLOR green}RAM  $memperc% ${membar}${color CD5C5C}
CPU1 ${cpu cpu1}% ${color CD5C5C}${cpubar cpu1}
CPU2 ${cpu cpu2}% ${color CD5C5C}${cpubar cpu2}${color }
${font Verdana:bold:size=9}${color 33ccff}${alignc} ${time %D}${color 008000}${font Verdana:bold:size=8}
${color 44ccff}${font :bold:size=12}${time %A} ${time %H:%M:%S}


have fun

---

