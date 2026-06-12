---
title: "conky setup"
date: 2012-07-18
forum: Desktop Environments
---

### Post by LulaLula on 2012-07-18
Hey! I found this nice conky theme, and i really want to try it. 

vg0rg0d.deviantart.com/art/Conqtpiky-172640511 

I have downloaded it and tried to install it. But it wont work. I got two text files, conkypi and conkypiclo and i dont know which i should put in conkyrc. 

i get an error message: This program is calling the Imlib call:

	imlib_context_free();

	With the parameter:

	context

	being NULL. Please fix your program.
------------------------------------------------------------
why is that? 

Can someone please guide me how to install this theme?

i use LXDE in Wattos.  

Thanks! :D

---

### Post by stinkeye on 2012-07-18
The included start script (conqtpi.sh) is written to load
```
conky -c ~/.conkypi &
conky -c ~/.conkypiclo
```

So rename **conkypi** and **conkypiclo** to **.conkypi**
and **.conkypiclo** and place in your home folder.
The preceding dot makes the files hidden.(To show hidden in the file browser...ctrl+h)

The path to the lua script in the conkypi config is **~/scripts/qtpi.lua**
so place **qtpi.lua** in **~/scripts**
Create the scripts folder if you don't have one.

Right click on the start script (conqtpi.sh) and properties > permissions
and mark execute.
Click on **conqtpi.sh** and run. Conky should start after 20secs.
Try the below fix for the Imlib errror before running.


Comment out the line in **~/.conkypi** that contains **${downspeedf ppp0}**...(Line #64)
eg
```
TEXT
${color FFFFFF}${goto 135}${voffset 75}${font Galga Bold:size=10}${swapperc}%${color ffffff}${voffset 12}${goto 130}${font Galga Bold:size=9}SWAP${font}${color ffffff}${goto 140}${voffset 12}${font RsbillsDng:size=15}w${font}
${color 000000}${goto 134}${voffset 28}${font Galga Bold:size=10}${fs_used_perc /}%${color 000000}${voffset 12}${goto 126}${font Galga Bold:size=9}FlSys${font}
${color ffffff}${goto 24}${voffset 65}${font Galga Bold:size=9}${memperc}%
${color ffffff}${goto 25}${font Galga Bold:size=9}RAM${font}  ${color ffffff}${voffset -12}${goto -30}${font RsbillsDng:size=15}H${font}
${color 000000}${goto 130}${voffset -30}${font Galga Bold:size=9}${battery_percent}%${color 000000}${voffset 12}${goto 133}${font Galga Bold:size=9}BAT${font}
${color 000000}${goto 135}${voffset 50}${font Galga Bold:size=9}${cpu cpu0}%${font}${color 000000}${voffset 12}${goto 134}${font Galga Bold:size=9}CPU${font}
[COLOR="Red"]#[/COLOR][COLOR="DimGray"]${color 000000}${goto 135}${voffset 110}${font Galga Bold:size=9}${downspeedf ppp0}K${font}${color 000000}${voffset 12}${goto 127}${font Galga Bold:size=9}MobDn${font}              ${color ffffff}${voffset -20}${goto}${font RsbillsDng:size=15}G${font}  ${color ffffff}${voffset -8}${goto -10}${font Galga Bold:size=9}${upspeedf ppp0}K${font}[/COLOR]
```

---

