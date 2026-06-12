---
title: "Xorg eat 90% of my CPU | i don't know why !! 0_o"
date: 2008-01-22
forum: Desktop Environments
---

### Post by Pegasus_from_UA on 2008-01-22
Hi
My Xorg system  load CPU since a bit time after start (5-15min).
TOP tell me:
```
top
```
```
Tasks: 152 total,   7 running, 144 sleeping,   0 stopped,   1 zombie
Cpu(s): 96.3%us,  3.0%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.3%hi,  0.3%si,  0.0%st
Mem:   1035784k total,  1021568k used,    14216k free,    96764k buffers
Swap:  1951856k total,    15348k used,  1936508k free,   307496k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5094 root      20   0  102m  72m  15m R 91.7  7.2 365:51.03 Xorg               
 6575 buzdack   15   0  233m 198m  17m R  6.3 19.6  33:16.72 opera              
11623 buzdack   15   0 49316  12m 1676 S  2.0  1.3  12:58.65 xskynet0897b6sb    
 5456 buzdack   15   0 61080  12m 9660 S  0.3  1.3   0:07.28 gnome-settings-    
29458 buzdack   15   0  2356 1192  888 R  0.3  0.1   0:00.03 top                
    1 root      15   0  2948 1856  532 S  0.0  0.2   0:01.25 init               
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.02 ksoftirqd/0        
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0    
```

and htop tell me it's gdm 
[[IMG]http://img216.imageshack.us/img216/9799/loadingtt6.th.png[/img]](http://img216.imageshack.us/my.php?image=loadingtt6.png)

I tried do next
```
sudo aptitude remove gmd
sudo aptitude install gmd

```
```
sudo aptitude remove xorg xserver-org
sudo aptitude install xorg xserver-org
```

I tried reinstall nVidia driver. I tried install them over console , by automatic program Envy...
Nothing...
Plese Help!

My System is
Ubuntu7.04
video: nVidia geForce 6600GT

---

