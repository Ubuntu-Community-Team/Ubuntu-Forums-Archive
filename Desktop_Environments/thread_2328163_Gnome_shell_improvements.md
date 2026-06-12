---
title: "Gnome shell improvements?"
date: 2016-06-18
forum: Desktop Environments
---

### Post by Omar_Jair on 2016-06-18
So on my long journey to find my ideal Ubuntu flavour i came across ubuntu gnome since gnome is the desktop ive used more but i know less of (Yes, as ironic as it sounds). So, my computer is not beefy but its pretty decent if we call it a laptop, the only problem is that i cannot have chromium, clementine or firefox open all in the same because it starts to get very very slow, i already decreased my swappy-thing value, i did manage to make Unity shell faster by disabling animations and special things with Compiz, is there any way to do something similar just to give GNOME shell a little more speed?:confused:

---

### Post by ajgreeny on 2016-06-18
Tell us more about the spec of that computer or we are all shooting in the dark.

Ubuntu-gnome needs approximately the same resources as Ubuntu with unity as far as I can make out, so depending on what spec you have you may find a lighter desktop is better for you.

---

### Post by RobGoss on 2016-06-18
Yes I think **Ajgreeny**, is correct lighter versions of Ubuntu might be the better option for your desktop. Here are just a few [Lubuntu ]("http://lubuntu.net/") or [Kubuntu]("http://kubuntu.org/") that comes to mind they use less resources

---

### Post by Omar_Jair on 2016-06-18
My computer has 4GB ram, using 3.7GB. 2 intel celeron processors of 2.16GHz, an Intel Bay Trail Graphics and 488GB free space, i dont know if you require more specs or how can i get more detailed results

About Kubuntu, i didn't knew that KDE desktop used less resources, ive had a bad trip with XFCE and KDE is way too slow for me.

---

### Post by Omar_Jair on 2016-06-19
So, is there anything i can do rather than switching desktops? i chose gnome shell because it ran pretty good on Debian and rarely gave me speed troubles.

---

### Post by RobGoss on 2016-06-19
At this point I would say try a lighter distribution and see how it goes. 

> [COLOR=#000000]My computer has 4GB ram, using 3.7GB. 2 intel celeron processors of 2.16GHz, an Intel Bay Trail Graphics and 488GB free space, i dont know if you require more specs or how can i get more detailed results[/COLOR]

Are you saying you're using 3.7GB of Ram out of 4GB?

---

### Post by Omar_Jair on 2016-06-19
Yes, 3.7 usable ram, i don't know how to change it to full use or if it is possible, any other light desktop environment that is not LXDE or XFCE? i know those are the lightest but i already use lxde on a very old computer and little mouse guy did not like me at all with wine apps, maybe mate?

---

### Post by RobGoss on 2016-06-19
Seeing you're having so much trouble with slowness this may be related to the **Intel Bay Graphics card. **Most of the time with low end graphics card these problems will arise. If I'm correct reading your **#4 **post you're also using most of your **Ram** but on what?

If you are wanting to do a clean install with** Lubuntu or Kubuntu, **I don't see any reason why the OS will not preform as it should

---

### Post by ajgreeny on 2016-06-19
I think the amount of ram shown is because the integrated graphics are using the 0.3GB of ram that is missing; I suspect that is the available amount, not the amount used, but show us the output of ```
free -m
```to check that in detail.

---

### Post by Omar_Jair on 2016-06-19
Did the command, here is the output
```
omar@Phantom:~$ free -m
              total        used        free      shared  buff/cache   available
Mem:           3839        1542         271         231        2025        1833
Intercambio:        3981           0        3981


``` , by now the most useful thing i can do is switch to my gnome flashback desktop to get a nice performance, as for the intel graphics card, is there anything that i can do to improve performance a little?

---

### Post by vasa1 on 2016-06-19
> **ajgreeny said:**
> I think the amount of ram shown is because the integrated graphics are using the 0.3GB of ram that is missing; I suspect that is the available amount, not the amount used, but show us the output of ```
free -m
```to check that in detail.
I too have Intel integrated graphics:
```
$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
$ grep -i chipset /var/log/Xorg.0.log
[    41.254] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
[    41.254] (II) VESA: driver for VESA chipsets: vesa
[    41.469] (--) intel(0): Integrated Graphics Chipset: Intel(R) GM45
$ 
```

```
$ free -m
              total        used        free      shared  buff/cache   available
Mem:           3914         532        2530          49         851        3112
Swap:          4056           0        4056
$ 
```
This with Lubuntu's Openbox session with Firefox and LibreOffice Writer open.

I'm wondering if it would be useful if OP ran```
top -n 1 -o %MEM
``` occasionally and reported back on what's hogging memory. Here's the output I see currently (just the top few):```
Tasks: 169 total,   1 running, 168 sleeping,   0 stopped,   0 zombie
%Cpu(s):  3.7 us,  0.7 sy,  0.0 ni, 92.6 id,  3.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem :  4008640 total,  2468308 free,   614984 used,   925348 buff/cache
KiB Swap:  4154364 total,  4154364 free,        0 used.  3075764 avail Mem 

  PID USER      %CPU %MEM COMMAND                                                                                                                                        
 2422 vasa1      0.0  9.8 firefox                                                                                                                                        
 1675 vasa1      0.0  3.7 dropbox                                                                                                                                        
 3067 vasa1      0.0  3.3 soffice.bin                                                                                                                                    
 1684 vasa1      0.0  1.3 kupfer                                                                                                                                         
  918 root       6.2  1.1 Xorg                                                                                                                                           
 1707 vasa1      0.0  0.9 nm-applet                                                                                                                                      
 2976 vasa1      0.0  0.6 lxterminal                                                                                                                                     
 1580 vasa1      0.0  0.4 openbox                                                                                                                                        
  693 root       0.0  0.4 NetworkManager                                                                                                                                 
 1662 vasa1      0.0  0.4 tint2                                                                                                                                          
  703 whoopsie   0.0  0.3 whoopsie                                                                                                                                       
 1978 root       0.0  0.3 udisksd                                                                                                                                        
  768 colord     0.0  0.3 colord                                                                                                                                         
 1750 vasa1      0.0  0.3 xfce4-power-man                                                                                                                                
 1668 vasa1      0.0  0.3 conky                                                         
```

---

### Post by Omar_Jair on 2016-06-20
Luckily i have a super DVD collection with most Ubuntu Flavours (Except Lubuntu & Kylin). @vasa did you manage to "Juice out" your intel card or my only hope is to switch to Lubuntu?

---

### Post by vasa1 on 2016-06-20
> **Omar_Jair said:**
> Luckily i have a super DVD collection with most Ubuntu Flavours (Except Lubuntu & Kylin). @vasa did you manage to "Juice out" your intel card or my only hope is to switch to Lubuntu?
Depends.

Please post the output of **top** as requested :)

---

### Post by Omar_Jair on 2016-06-20
Here is the output
```
omar@Coffee:~$ top -n 1 -o %MEM

top - 16:27:35 up  1:20,  2 users,  load average: 0.70, 0.98, 1.10
Tareas: 181 total,   1 ejecutar,  180 hibernar,    0 detener,    0 zombie
%Cpu(s): 27.1 usuario,  8.8 sist,  2.3 adecuado, 58.8 inact,  2.6 en espera,  0.
KiB Mem :  3931220 total,   541400 free,  1009876 used,  2379944 buff/cache
KiB Swap:  4077564 total,  4077564 free,        0 used.  2562868 avail Mem 

  PID USUARIO   PR  NI    VIRT    RES    SHR S  %CPU %MEM     HORA+ ORDEN       
 4093 omar      20   0 1536536 445864 109796 S   0.0 11.3   4:54.39 firefox     
31548 omar      20   0 2002824 275188  39168 S   6.2  7.0   4:02.02 IMVUClient+ 
 3757 root      20   0  465612 150352  73860 S   0.0  3.8   1:27.36 synaptic    
 1640 root      20   0  305548  69076  56496 S   0.0  1.8   5:15.21 Xorg        
 5387 omar      20   0  501980  68816  49924 S   0.0  1.8   0:02.54 plugin-con+ 
 3057 omar      20   0 1213432  62308  37516 S   0.0  1.6   0:07.62 caja        
 3093 omar      20   0  854996  57740  36396 S   0.0  1.5   0:01.25 blueman-ap+ 
 3130 omar      20   0  516872  38232  28548 S   0.0  1.0   0:00.83 tilda       
 3101 omar      20   0  666532  37004  30400 S   0.0  0.9   0:01.79 nm-applet   
 3038 omar      20   0  864380  36404  27724 S   0.0  0.9   0:04.28 mate-panel  
 3034 omar      20   0 1123372  33852  26140 S   0.0  0.9   0:03.97 mate-setti+ 
 3273 omar      20   0  704312  33656  24916 S   6.2  0.9   0:50.50 marco       
 5406 omar      20   0  781316  31568  25728 S   0.0  0.8   0:00.32 mate-termi+ 
 3137 omar      20   0  243860  31444  14844 S   0.0  0.8   0:00.75 applet.py   
 3062 omar      20   0  701700  31356  24740 S   0.0  0.8   0:05.41 wnck-applet 
 3098 omar      20   0  623928  30388  24812 S   0.0  0.8   0:00.67 polkit-mat+ 
 3142 omar      20   0  526928  29580  24500 S   0.0  0.8   0:00.46 update-not+
```

---

### Post by vasa1 on 2016-06-21
```
  PID USUARIO   PR  NI    VIRT    RES    SHR S  %CPU %MEM     HORA+ ORDEN       
 4093 omar      20   0 1536536 445864 109796 S   0.0 11.3   4:54.39 firefox     
31548 omar      20   0 2002824 275188  39168 S   6.2  7.0   4:02.02 IMVUClient+ 

```So that's not too bad?

I don't bother about RAM usage until things go wonky. Are you using compositing? You seem to have quite a few Mate applications as well?

I don't know if you've seen [http://www.linuxatemyram.com/](http://www.linuxatemyram.com/) but it's worth a look.

---

### Post by Omar_Jair on 2016-06-21
Yeah im now in MATE, tried to do a Flavor Swap but did not go too well, had to reinstall Ubuntu but MATE seems pretty good, RAM never passes 2BG now, maybe i could stick to GNOME2, i just got notified it's Ubuntu MATE 2nd Birthday.

---

