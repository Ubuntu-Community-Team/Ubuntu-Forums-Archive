---
title: "on Kubuntu cant go 1920x1080"
date: 2021-11-01
forum: Desktop Environments
---

### Post by devdlp on 2021-11-01
i have seen this on some forums but i still have this problem with the screen not going 1920x1080 on my main monitor the other one does which is smaller.
but not this big tv i have.
its a vizio if that helps its at default right now becuase i dont know what to do with the resolution.
but i literally need 1920x1080p becuase i cant work right on it like i want to.
please someone move me in the right direction.
its kubuntu 20.04, nvidia 1050 ti both monitors plugged into it and nvidia drivers installed.
thanks in advance.

---

### Post by ActionParsnip on 2021-11-02
What is the output of
```

sudo lshw -C display
lsb_release -a
uname -a
xrandr

```
Thanks

---

### Post by devdlp on 2021-11-02
[FONT=monospace][COLOR=#000000]sudo lshw -C display [/COLOR]
[sudo] password for tahm:  
  *-display                  
       description: VGA compatible controller 
       product: GP107 [GeForce GTX 1050 Ti] 
       vendor: NVIDIA Corporation 
       physical id: 0 
       bus info: pci@0000:01:00.0 
       version: a1 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom 
       configuration: driver=nvidia latency=0 
       resources: irq:37 memory:f5000000-f5ffffff memory:d0000000-dfffffff memory:e00000
00-e1ffffff ioport:e000(size=128) memory:f6000000-f607ffff 
  *-display 
       description: VGA compatible controller 
       product: Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller 
       vendor: Intel Corporation 
       physical id: 2 
       bus info: pci@0000:00:02.0 
       version: 06 
       width: 64 bits 
       clock: 33MHz 
       capabilities: msi pm vga_controller bus_master cap_list rom 
       configuration: driver=i915 latency=0 
       resources: irq:33 memory:f6400000-f67fffff memory:c0000000-cfffffff ioport:f000(s
ize=64) memory:c0000-dffff
[/FONT]
[FONT=monospace][FONT=monospace][COLOR=#000000]lsb_release -a [/COLOR]
No LSB modules are available. 
Distributor ID: Ubuntu 
Description:    Ubuntu 20.04.3 LTS 
Release:        20.04 
Codename:       focal

[/FONT]

[/FONT]

---

### Post by devdlp on 2021-11-02
> **ActionParsnip said:**
> What is the output of
```

sudo lshw -C display
lsb_release -a
uname -a
xrandr

```
Thanks

[FONT=monospace][COLOR=#000000]uname -a [/COLOR]
Linux tahm-MS-7850 5.11.0-38-generic #42~20.04.1-Ubuntu SMP Tue Sep 28 20:41:07 UTC 2021
 x86_64 x86_64 x86_64 GNU/Linux 
[COLOR=#54ff54]**tahm@tahm-MS-7850**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ xrandr [/COLOR]
Screen 0: minimum 8 x 8, current 3280 x 1080, maximum 32767 x 32767 
DVI-D-0 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 527mm x 296mm 
   1920x1080     60.00*+  60.00    59.94    50.00    50.00    60.00    50.04   
   1680x1050     59.95   
   1440x900      59.89   
   1280x1024     60.02   
   1280x800      59.81   
   1280x720      60.00    59.94    50.00   
   1152x864      75.00   
   1024x768      70.07    60.00   
   800x600       60.32    56.25   
   720x576       50.00   
   720x480       59.94   
   640x480       59.94    59.93   
HDMI-0 connected primary 1360x768+1920+0 (normal left inverted right x axis y axis) 700m
m x 400mm 
   1360x768      60.02*+ 
   1920x1080     60.00    59.94    50.00    29.97    23.98    60.05    60.00    50.04   
   1280x768      59.87   
   1280x720      60.00    59.94    50.00   
   1024x768      60.00   
   800x600       60.32   
   720x576       50.00   
   720x480       59.94    59.94   
   640x480       59.94    59.93   
DP-0 disconnected (normal left inverted right x axis y axis) 
DP-1 disconnected (normal left inverted right x axis y axis) 
VGA-1-1 disconnected (normal left inverted right x axis y axis) 
HDMI-1-1 disconnected (normal left inverted right x axis y axis) 
HDMI-1-2 disconnected (normal left inverted right x axis y axis)

[/FONT]

---

### Post by devdlp on 2021-11-02
i forgot to mention when i do switch it to 1920x1080 its a bit off some things are off the screen sorry for not putting that in earlier

---

### Post by devdlp on 2021-11-02
fixed IT!!!!
THIS
             
[LIST]
[*]                                   
         
                                                        I'd suggest formatting this as a bulleted list so more people will see it. It is the correct answer for 14.04 and nVidia.                                 &#8211; [semitones]("https://askubuntu.com/users/74067/semitones")                 
                 [Feb 25 '15 at 21:18]("https://askubuntu.com/questions/4358/how-do-i-fix-overscan-on-my-hdmi-hdtv#comment819665_471199")             
         

[*]                                   
         
                                                        I'm not sure if this does the same thing as the slider, but I found setting the viewportout=1776x999+96+54  in the NVidia XServer Settings solved the problem for my TV, which only  has the option to not overscan when using the VGA connector but not any  HDMI connector. My TV is about the same vintage as these answers!                                 &#8211; [Don 01001100]("https://askubuntu.com/users/234253/don-01001100")                 

                 [May 18 '20 at 4:53]("https://askubuntu.com/questions/4358/how-do-i-fix-overscan-on-my-hdmi-hdtv#comment2090596_471199")                                                                                            

         
[/LIST]
 	    
from!!!
[https://askubuntu.com/questions/4358/how-do-i-fix-overscan-on-my-hdmi-hdtv](https://askubuntu.com/questions/4358/how-do-i-fix-overscan-on-my-hdmi-hdtv)

---

