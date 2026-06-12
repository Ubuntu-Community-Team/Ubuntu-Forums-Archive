---
title: "100% CPU usage when playing any simple avi or mpeg media files.Really need help"
date: 2009-06-11
forum: General Help
---

### Post by ubfu on 2009-06-11
Ubuntu 8.04
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3870
AMD2 4000+ 2.10 GHz

Once I play a media file such as avi or mpeg , the cpu usage increase to 100%

The Xorg is using a 83- 90 % of usage.

```
top - 20:55:20 up  2:25,  2 users,  load average: 0.59, 0.45, 0.40
Tasks: 123 total,   4 running, 119 sleeping,   0 stopped,   0 zombie
Cpu(s): 51.0%us,  1.5%sy,  0.0%ni, 47.5%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2074592k total,  2022932k used,    51660k free,   286564k buffers
Swap:  4112600k total,        0k used,  4112600k free,  1204760k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5448 root      20   0  401m  86m  30m R   91  4.3  24:32.44 Xorg               
10580 ng        20   0  144m  30m  17m S   12  1.5   0:03.36 vlc                
 5769 ng        20   0 39580 8336 4188 R    5  0.4   0:23.39 pulseaudio         
 5864 ng        20   0 24416  17m 6840 S    1  0.8   0:52.99 compiz.real        
 9018 ng        20   0 65668  19m  10m S    1  0.9   0:03.88 gnome-terminal     
 5939 ng        20   0 45796  16m  10m R    0  0.8   0:05.42 mixer_applet2      
    1 root      20   0  2844 1688  544 S    0  0.1   0:01.34 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.04 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.10 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.06 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper   
```

On my window xp , playing the same files doesn't use 15% cpu usage.

I really need help on this.I just started to install Ubuntu yesterday and now I am facing a lot of problem.
-Audio problem [http://ubuntuforums.org/showthread.php?p=7438541#post7438541](http://ubuntuforums.org/showthread.php?p=7438541#post7438541)
-Ati driver installation problem [http://ubuntuforums.org/showthread.php?t=1184346](http://ubuntuforums.org/showthread.php?t=1184346)

---

### Post by keplerspeed on 2009-06-11
Have you enabled visual effects? Ah it appears so by top.

Disable visual effects and then see what the media playback is like.

---

### Post by ubfu on 2009-06-11
> **keplerspeed said:**
> Have you enabled visual effects? Ah it appears so by top.

Disable visual effects and then see what the media playback is like.

Thanks! it works:D:D[-o<

I tested it again 

None - CPU usage is under 30%
Normal - CPU is 100%
Extra - The whole PC screen blackout and I need to press reset button on my PC.

What is the main culprit that cause this kind of effect problem ? 
I was wondering , my PC specification was at middle range , shouldn't be having any problem handling any extra visual affect.

Anyone guide me on how to fix it ? I guess most of the ubuntu user here is using either normal or extra visual effect that runs well.

Thank you , hope someone can fix this bug.

---

### Post by lovinglinux on 2009-06-11
> **ubfu said:**
> Thanks! it works:D:D[-o<

I tested it again 

None - CPU usage is under 30%
Normal - CPU is 100%
Extra - The whole PC screen blackout and I need to press reset button on my PC.

What is the main culprit that cause this kind of effect problem ? 
I was wondering , my PC specification was at middle range , shouldn't be having any problem handling any extra visual affect.

Anyone guide me on how to fix it ? I guess most of the ubuntu user here is using either normal or extra visual effect that runs well.

Thank you , hope someone can fix this bug.

Go to "System >> Administration >> Hardware Drivers" and check if you have the latest ATI driver enabled.

---

### Post by ActiveFrost on 2009-06-11
You need to enable your video card driver ( for most of cards ). I had the same issue with my Nvidia video card :)

---

### Post by ubfu on 2009-06-11
> **lovinglinux said:**
> Go to "System >> Administration >> Hardware Drivers" and check if you have the latest ATI driver enabled.

I had manually install Ati driver going though the Ati driver website downloaded the.deb and install.

It gives me a lot of trouble installing and finally successful.[http://ubuntuforums.org/showthread.php?t=1184346](http://ubuntuforums.org/showthread.php?t=1184346)

How do I test whether I successfully installed ?

---

### Post by ubfu on 2009-06-12
Please anyone know the problem ? 
What steps I should made ?

---

### Post by ubfu on 2009-06-12
Anyone successfully runing extra visual effect and video with an AMD 64 x2 2.0Ghz with a decent graphic card like Ati 3650 hardware ?

---

### Post by ubfu on 2009-06-12
Request for help.
Why my swap files is 0 ? Should at lease use 100mb.

Mem:   2074592k total,  2022932k used,    51660k free,   286564k buffers
Swap:  4112600k total,        0k used,  4112600k free,  1204760k cached

Why does my memory used that much ? is it because of the visual effect ?

Really hope someone will give out their visual configuration.

---

### Post by ubfu on 2009-06-23
How to disable xorg ?

---

### Post by ubfu on 2009-06-25
Please anyone can help me :(:(
Anyone know how I can notified expert at launchpad to check my error ?
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/390995](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/390995)

---

