---
title: "Conky Problem getting data formatted correctly"
date: 2008-01-04
forum: Desktop Effects &amp; Customization
---

### Post by BijuMathew on 2008-01-04
Hello all,
 Ive configured Conky for my Ubuntu box and everything is well but just a small problem.
The temperatures for my HDD , CPU and FSB seem to have a weird character that looks like an A before the degree C sign. Does anyone know how to fix it. At this point I'm clueless. I was able tog et it to work with my temperature which required editing pogodynka.sh . However no matter how hard I try I cant edit the other ones correctly. I have attached the screenshot of my conly here and its configurations. Would appreciate any help. 

[[IMG]http://img502.imageshack.us/img502/8181/screenshotdesktopof1.th.png[/IMG]](http://img502.imageshack.us/my.php?image=screenshotdesktopof1.png)

My .conkyrc file is given here 

```

use_xft yes
xftfont Dejavu Sans:size=8
alignment top_right
TEXT
${font weather:size=42}${execi 600 ~/scripts/conditions.sh}${font}${voffset -10}  ${execi 1200 ~/scripts/pogodynka.sh}

    ${font weather:size=28}x ${font}HDD ${execi 1 ~/scripts/hddmonit.sh}°C 
    ${font weather:size=28}z ${font}CPU ${i2c temp 2}°C 
    ${font weather:size=28}y ${font}FSB ${i2c temp 1}°C
    
   ${font PizzaDude Bullets:size=16}v${font}   Up. ${upspeed eth0} Kb/s 
   ${font PizzaDude Bullets:size=16}r${font}   Dow. ${downspeed eth0} Kb/s 

   ${font PizzaDude Bullets:size=16}M${font}   Upload. ${totalup eth0}
   ${font PizzaDude Bullets:size=16}S${font}   Download. ${totaldown eth0}
   
   ${font StyleBats:size=18}A${font}   CPU:  ${cpu}%
   ${font PizzaDude Bullets:size=16}J${font}   $mem / $memmax

   ${font StyleBats:size=18}P${font}   Work:  ${uptime_short}
   ${font StyleBats:size=18}4${font}   ${time %A %d %B}

   ${font xspiralmental:size=17}E${font}   ${kernel}

```

My hddmonit.sh

```

#!/bin/bash
echo "$(nc localhost 7634 | cut -d'|' -f4)"

```

I doubt the other files like pogodynka.sh is required since it deals with the weather part which I have no problem with. 

Any help would be appreciated.
Thanks

---

### Post by lvleph on 2008-01-04
Delete

---

### Post by BijuMathew on 2008-01-04
> Delete 

Delete what?

---

### Post by psyopper on 2008-01-04
It looks like you are using ```
i2c temp 2
``` to get your temperature readings. COnky works very much like the terminal, so what happens if you run these commands in the terminal? Do you get the same thing?

If you do you can grep/cut the results to remove the unwanted characters. For instance, here's how I get my CPU name:
```

${execi 1000 cat /proc/cpuinfo | grep "model name" | cut -c14-36}

```

Specifically it's ```
cat /proc/cpuinfo | grep "model name" | cut -c14-36
``` that runs identically in the terminal. Use *man grep* if you need more help on using grep or   *man cut* to figure out how to cut out (or in) what you need.

---

### Post by BijuMathew on 2008-01-04
Thank you for your reply :). Im able to retrieve the temperature with no problem. Its the way the data is formatted that bothers me. Somehow when the data is extracted the degree sign (o) is displayed as a weird A character followed by the (o) symbol as shown in the screenshot. I can
t figure out why it would work in the case of weather readings while it wont work in the case of the temperatures of the HDD, CPU etc.

---

