---
title: "Anyone using KDE 4?"
date: 2008-04-18
forum: Desktop Environments
---

### Post by Kiri on 2008-04-18
I'm thinking about trying out KDE in my standard Ubuntu (gnome version) install. 
I'm wondering if I should install the old stable KDE or give the new KDE 4 a try. 
Is anyone using KDE 4 yet? and how is it?
I don't mind if its not 100% stable, but at least functional.

---

### Post by GeneralZod on 2008-04-18
Put it this way: Quite a lot of KDE *developers* are still using KDE3 ;) Give it a whirl if you're really curious, but I'd advise using KDE3 for the time being.

Hopefully, KDE4.1 (due end of July, if all goes according to plan) will be a big improvement over 4.0.x, although I suspect it won't really hit its stride until 4.2 or so.

---

### Post by .nedberg on 2008-04-18
> **GeneralZod said:**
> Put it this way: Quite a lot of KDE *developers* are still using KDE3 ;) Give it a whirl if you're really curious, but I'd advise using KDE3 for the time being.

Hopefully, KDE4.1 (due end of July, if all goes according to plan) will be a big improvement over 4.0.x, although I suspect it won't really hit its stride until 4.2 or so.

+1

O my main desktop i use KDE3, on a spare laptop I have fun with KDE4. KDE4 is nice and fun, but not that usable in my oppinion.

---

### Post by Kiri on 2008-04-18
thanks guys/ I think I will give KDE 3 a try then.

I mainly just want to try it to see if multi-monitor support is better in KDE than gnome anyway.

---

### Post by der_joachim on 2008-04-18
I for one prefer KDE4 over KDE3. I am not a developer. Merely a glutton for punishment. :)

I can personally work very well with it, but I do not recommend it to anyone else. It is not done yet. Pretty though...

---

### Post by Kiri on 2008-04-19
I tried out KDE 3 last night. 
I have to say I did like it. 
The good thing was it seemed more customizable than gnome. But the bad point was it seemed a little more confusing to configure since there are so many settings. 
I also thought it felt snappier than gnome and more responsive. 
But the best thing I thought was some of the basic apps it comes with. Especially like dolphin for file management. It is still quite basic I guess, but dual pane and nicely designed. I really do not like nautlius at all..

Unfortunately it did not solve any of my problems with multimonitor setups and I had all the same problems that I had in gnome when trying to get them working.
(I am trying to get twinview to work with my primary monitor to the right instead of to the left. Sounds simple, but it is actually really difficult / so far impossible)

---

### Post by .nedberg on 2008-04-19
Do you use Nvidia?

Have a look in /etc/X11/xorg.conf. Look for a line with
```
Option "TwinViewOrientation" "xxx"
```
substitute xxx with RightOf or LeftOf. This would work with both Gnome and KDE as it does not have anything to do with those.

---

### Post by Kiri on 2008-04-19
Hey .nedberg, I gave that a try but it didn't seem to have any effect.  To be honest I really do not understand the xorg.conf file very well.

I tried adding this line:

```
Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option	   "TwinViewOrientation" "RightOf"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +1920+400; CRT: NULL, DFP: nvidia-auto-select +0+0"
EndSection

```


Perhaps because I have the positions defined already as absolute positions...
But I can get the monitors in the right position, its just that the DE puts all the icons etc on the far left monitor, rather than the right one (which should be primary).  Seems to be just the way it is unfortunately :(

---

### Post by .nedberg on 2008-04-19
Hi

Yes, xorg.conf is intimidating! I am no expert myself, but I got it working. One error in your file is that the twinview options go in the Device section. Here is my device section in my xorg.conf
```
Section "Device"
        Identifier      "nVidia Corporation NV43 [GeForce 6600 GT]"
        Driver          "nvidia"
        Busid           "PCI:5:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "False"
#Following added 2007-10-20
        Option "Twinview" "true"
        Option "MetaModes" "1280x1024,1280x1024; 1280x1024,1024x768; 1024x768,1024x768"
        Option "SecondMonitorHorizSync" "30-65"
        Option "SecondMonitorVertRefresh" "50-75"
        Option "ConnectedMonitor" "CRT, CRT"
        Option "TwinViewOrientation" "RightOf"
EndSection
```
You can see the options I added.

If the monitors have the same resolution you could try to switch outputs. It could work...

Just for comparison here is my Screen section
```
Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV43 [GeForce 6600 GT]"
        Monitor         "CMC 19 AD"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1280x1024"     "1152x864"      "1024x768"      "832x624"       "800x600"       "720x400"       "640x480"
        EndSubSection
EndSection

```

Remember to back up your original file before you edit it!!!!!!!

---

