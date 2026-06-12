---
title: "hddtemp and superkaramba"
date: 2006-01-09
forum: General Help
---

### Post by floyd27 on 2006-01-09
hi all.
i have a monitor running in SK. 
i managed to get all the sensors working and configured except HDD temp..
I installed hddtemp and I can run it in a terminal fine (sudo hddtemp /dev/sda)
I cannot get it to work if i dont "sudo" though..

I cant get the system monior to show any temp related to it.
i tried..
everything in the monitor config file looks good..


................................................................................................
(text x=64 y=60 value="Temp" color=255,255,255 align=left fontsize=10 font="sans"
bar x=109 y=65 w=100 h=5 vertical=false path="img/bar.png" interval=60000 sensor=program program="hddtemp /dev/sda | awk '{print $3}' | cut -c 1,2" max=60
text x=200 y=60 sensor=program program="hddtemp /dev/sda | awk '{print $3}'" format="%v°C" interval=60000 align=right color=255,255,255 fontsize=10 font="sans"
....................................................................................................

-reloaded the theme after each try...
-Sudo modprobe hddtemp and (hddtemp /dev/sda) but there is no module...
-everything looks Ok but there is no temp in the monitor.

Is there somethng im missing? permissions/modprobe? any help would be great..
thanx

---

### Post by stevec on 2006-01-09
When you set up hddtemp you must set it as SUID root

Type      sudo dpkg-reconfigure hddtemp

You can configure to set SUID as root then it should work ok.

---

### Post by floyd27 on 2006-01-10
that did it thanx..

---

