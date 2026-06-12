---
title: "Programs freezing up, Volume icon flashing"
date: 2009-02-16
forum: General Help
---

### Post by lizard08 on 2009-02-16
I'm having trouble with Ubuntu 8.10 freezing up. It has been happening quite often and I'm having to restart my computer at least every half hour (for example, the first time I tried typing this.) I have a new Toshiba Sattelite U305. Here is what happens- I'll have a program open and the volume icon will appear in the middle of the screen and start flashing. Then if I try clicking or typing anything in the program or on the top toolbar, nothing will happen. I'll still be able to close windows and click on certain things, but nothing else will work. 
Does anyone know what causes this or how to fix it?
Thanks, 
Liz

---

### Post by Gen2ly on 2009-02-16
Unsure of what causing theproblem, my first recommendation is to run "top" from the terminal.  Find out what is hogging the cpu.  If your hard-drive is paging alot, look into iotop definitely.  Looks like some program is in overrun.  If you find that package that is in error, try to update, or perhaps even better - downgrade.

---

### Post by lizard08 on 2009-02-16
I checked top, and my computer is not frozen right now but Picasa is using 10% CPU. It's been crashing a lot while I'm doing photo editing on GIMP or Picasa.

---

### Post by lizard08 on 2009-02-16
This is what is showing. 

 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND           
 8961 lizard    20   0 2605m  31m 9912 S    7  1.6   0:06.77 Picasa2.exe       
 6831 lizard    20   0  4296 1724  640 S    3  0.1   0:25.82 wineserver        
 5362 root      20   0  406m  63m 9560 S    2  3.1   1:40.61 Xorg              
 6113 lizard    20   0 10792 3412 2936 S    0  0.2   0:00.40 gdl_config        
 7111 lizard    20   0 2592m 8880 5912 S    0  0.4   0:07.34 PicasaMediaDete   
 8976 lizard    20   0  2416 1160  876 R    0  0.1   0:00.20 top               
 6115 lizard    20   0 71832 5664 3844 S    0  0.3   0:35.45 gdl_fs_crawler    
    1 root      20   0  3056 1900  576 S    0  0.1   0:01.38 init              
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd          
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0       
    4 root      15  -5     0    0    0 S    0  0.0   0:00.44 ksoftirqd/0       
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0        
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1       
    7 root      15  -5     0    0    0 S    0  0.0   0:00.38 ksoftirqd/1       
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1        
    9 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/0          
   10 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/1

---

### Post by Gen2ly on 2009-02-17
Don'tthink I see anything there (next time wrap [code] around it please).  keep it on until your freezes, like I said you might want to try iotop too.

D

---

