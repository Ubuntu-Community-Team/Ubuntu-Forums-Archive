---
title: "CPU usage is really high"
date: 2010-02-03
forum: Gaming &amp; Leisure
---

### Post by MLColejr on 2010-02-03
I am a new user to Ubuntu, and I am so happy to have left Windows behind but I am having an issue with playing games like Armagetron advanced and Tremulous. My CPU goes thru the roof but i m barely touching my memory and all games are lagging bad even when played locally. I played splinter cell and world of warcraft on the same machine with win XP with no lag issues. Is there something I did during setup or something I can change to maximize the performance of my machine? Any help would be appriciated.

Ubuntu 9.1
AMD 64 X2 2.1Ghz CPU
2 GB ddr2 800 Mhz Ram
nvidia 7600 GT 256mb video card
western digital 500gb 7200 rpm HDD

---

### Post by davec64 on 2010-02-03
I'm not into gaming but you could try the following.

use TOP in a terminal to identify which processes are hogging the CPU, this will enable you to search further on the forums for a solution.

```
top
```

You could also try turning off Desktop Affects (Compiz).

Another think to try is the different Nvidia drivers, they may or may not hve an effect in your situation.

Hope that helps! :)

---

### Post by MLColejr on 2010-02-03
This is the info i get from TOP command. thnx BTW. I am looking to see which drivers work best for video card and I have had my visual affect set at (none) since install because of my windows games running in wine.(also very slow but whole different issue) Thnx again for the help.

P.S. I have installed the recommended diver for my Nvidia 7600GT card (which gave me errors on the first try) and it seems to be working fine but games are still lagging. These games are not highly intensive games so I'm not sure why they're loading up on the CPU like this. I can't find a way to check the GPU usage to see if its even working like it should. thnx again for any help
home@home-desktop:~$ top

top - 16:24:47 up 14:23,  2 users,  load average: 1.12, 1.10, 1.05
Tasks: 149 total,   1 running, 148 sleeping,   0 stopped,   0 zombie
Cpu(s): 48.7%us, 10.0%sy,  0.0%ni, 41.2%id,  0.0%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:   2060680k total,   936624k used,  1124056k free,   150680k buffers
Swap:  6032368k total,        0k used,  6032368k free,   455988k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND          
 3053 home      20   0  123m  26m  11m S  100  1.3  81:54.69 armagetronad.re  
 3558 home      20   0 37744  12m 9420 S   11  0.6   0:06.22 gnome-terminal   
 3264 home      20   0  307m  95m  29m S    3  4.7   2:38.48 firefox          
 1125 root      20   0 74428  53m  12m S    2  2.7  25:34.59 Xorg             
 1400 home      20   0  156m 5148 3920 S    1  0.2   7:01.10 pulseaudio       
    1 root      20   0  2652 1540 1128 S    0  0.1   0:00.99 init             
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd         
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0      
    4 root      15  -5     0    0    0 S    0  0.0   0:00.02 ksoftirqd/0      
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0       
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1      
    7 root      15  -5     0    0    0 S    0  0.0   0:00.68 ksoftirqd/1      
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1       
    9 root      15  -5     0    0    0 S    0  0.0   0:00.14 events/0         
   10 root      15  -5     0    0    0 S    0  0.0   0:00.21 events/1         
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 cpuset           
   12 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper

---

### Post by portets on 2010-02-03
looks like armegatron is hogging. is that a game?

---

### Post by davec64 on 2010-02-03
Had a search for you and came up with this as armagetronad is at 100%, rom the armagetron Wiki here:

[http://wiki.armagetronad.net/index.php?title=FAQ#ArmagetronAd_takes_most_or_all_the_CPU_time.2C_how_come.3F]("http://wiki.armagetronad.net/index.php?title=FAQ#ArmagetronAd_takes_most_or_all_the_CPU_time.2C_how_come.3F")

> ArmagetronAd takes most or all the CPU time, how come?

AA takes all the CPU time it needs to simulate and render the scene as fast as you'll allow it to. There are two conditions under which that makes it take almost everything that is available:

    * You set your graphics card driver not to wait for VSync. AA will then run at the highest possible framerate and therefore also use all the CPU time available. If you enable the FPS display in the HUD options and it shows more than 100 FPS, then that's your problem.
    * When it tells your video card driver to update the screen now, the driver goes into a special CPU-hogging mode until the command is completed, even though all it does is sit around and wait. Both NVidia and ATI drivers are guilty of this. In the "Performance Tweaks" submenu of the graphics settings, there is the "Flush" menu item where you can tweak AA to not issue the problematic command (with possible side effects). 

I suggest you have a look and see if these fixes might apply. :)

---

### Post by MLColejr on 2010-02-04
Very cool; the performance tweaks worked thnx so much. I guess looking at a readme file wouldn't hurt next time lol thnx again problem solved. just selected the finish option instead of flush it pulls on the cpu but keeps the framerates down so not to over work it to the point of lag.

---

### Post by davec64 on 2010-02-04
Glad to be of help!

All the best

---

