---
title: "CPU overheating on dell d630 i8kutils"
date: 2010-07-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vangop on 2010-07-26
Hi,
Dell d630 used to overheat sometimes and shut down.
```
$ cat /proc/acpi/thermal_zone/THM/trip_points 
critical (S5):           104 C

```
This happened on system backup with tar-bzip, avi editing in avidemux - high cpu tasks. 
While trying to solve this I installed i8kutils. Running it manually with values:
```
$ cat .i8kmon 
set config(0) {{- 0}  -1  55  -1  60}
set config(1) {{- 1}  50  65  50  65}
set config(2) {{- 2}  55  128  55  128}
```
I've adjusted 1000->200 as described [here]("http://ubuntuforums.org/showpost.php?p=5434295&postcount=3")
Now the situation is even worse. Laptop is shutting down while watching youtube, t jumps to critical 104 right after I start some encoding in avidemux.
without i8kmon t is the same or on the edge 98-102.
So ubuntu is controlling the fans regardless i8k. i8kmon seems to be competing with the system for control.
I also noticed that level 2 (max) of i8kmon is  less than the max fan I heard before installing i8k.
Can anybody enlighten me on this? Should I remove i8kutils and go on with the system control or just tune i8kmon?
I never had these problems on windows, it never shut down out of overheating so the fans are controlled better there?
the max speed the fan has now is ~4000 rpm. I'm using a 0.033 coef in sensors applet as advised [here]("https://bugs.launchpad.net/ubuntu/+source/sensors-applet/+bug/200449"). As without this the values are >100k..

---

### Post by vangop on 2010-07-27
Nobody has fan/heat issues?

---

### Post by Krabby.Linux on 2010-07-27
Hmm , just recognized that my cpu is >90 and critical ... There is just music and Firefox running ... Hmmm. Have a XPS Notebook.

---

### Post by jonsson on 2011-04-11
I have similar problems, did you solve them? For quite some time now I've felt that my D630 was sometimes very slow. After installing some CPU monitoring widget I realised that my CPU gets stuck at 800 Mhz because it gets too hot.

Since I never heard the fan anymore and it didn't seem to be running I just assumed my fan was broken. Yesterday I finally replaced it but the problem is still there. I've just installed i8kutils now to see if that might do the trick. With that I can at least manually make the fan run. Letting the laptop cool down now, will then reboot and try i8kmon i daemon mode with a custom config that should have the fan running quite often.

---

### Post by jonsson on 2011-06-19
Just wanted to report that in my case the problem seems to initially have been dust that prevented the fan from running and then I installed a fan that turned out not to be 100% compatible. After cleaning the original fan an putting it back in, everything works fine. :)

---

### Post by gradinaruvasile on 2011-06-19
> **vangop said:**
> Nobody has fan/heat issues?


Be careful with high cpu tasks. I have a d630 and i had to replace the mobo because the video card (nvidia nvs 135M) fried.

Laptops are not made for long-term high cpu tasks. They tend to get very hot because there is little room to cool them (unlike desktops that have plenty of air flowing in the case and most circuits are directly exposed to it).
Any cooling solution will help it cool faster, but you will still get high temperature peaks.

Solutions: put the desktop only on hard surfaces, not on bed/sofa/etc - the laptop has air vents on the side and on the bottom.
Better yet, use an external laptop cooler (this is a support that has fans on it, usually powered from USB ports. This is a solution i use and really helps bringing the temps down.


BTW sensors supports the laptop fully (issue a "sensors-detect" first) - you have per-core temperatures and mobo temps aswell.

I made a little script that monitors the GPU and triggers the fan on max if the GPU temp reaches a certain amount of degrees (63 is the default threshold). You have to adjust it to your needs.
The fan will intermittently work on full throttle for a sec then scale back down for a second then back to full again because the BIOS/i8kmon wants it on speed 1.
Here it is:

```

#!/bin/bash
if test -z "$1"
 then 
  goodtemp=63
 else
  goodtemp=$1
fi

while [ 1 = 1 ]
 do
  realtemp=`nvclock -T | grep GPU |cut -d \  -f 4 | cut -d \C -f 1`
  sleep 2
   if [ $realtemp -gt $goodtemp ]
    then

     echo "GPU temp $realtemp degrees, fan throttling needed"
     /usr/bin/i8kfan {} 2
     notify-send -t 1185 -u low -i $HOME/bin/icons/nvclocklogo-small.png "GPU temperature alert! Critical treshold: $goodtemp " "GPU internal sensor reports $realtemp degrees, fan starting at full throttle"
     #sleep 1
     
    else
	 echo "Temperature in safe range"
	 sleep 2
   fi
done


```

---

