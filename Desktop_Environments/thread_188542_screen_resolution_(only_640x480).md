---
title: "screen resolution (only 640x480)"
date: 2006-06-04
forum: Desktop Environments
---

### Post by RoyalShrubber on 2006-06-04
Sorry because I am complete n00b in linux (but experienced with windows), so please help me repair my problems

During installation (LiveDVD) of my Ubuntu (Dapper Drake 6.06) I enjoyed normal screen resolution of 1600x1200 (normally I use 1280x1024 but it was ok).

Then after rebooting and opening real Ubuntu installation the screen resolution was 640x480. So looked arround and in menues I found configuration tool that should change res. But there was only one option: 640x480 and 60hz. That's strange, why does liveDVD show right resolution and real not? I even restarted linux and it didn't help. So I went on internet (with my xp) to find a solution, and i found that i should check /etc/X11/xorg.conf. I opened it and it seemed ok... so I tried to delete the section with resolutions (in hope linux would rebuild them) but I wasn't able to save (some presmission stuff). If the solution is in changing xorg.conf file please tell me how can I get those (root?) permissions. I also saw on internet that if liveCD xorg.conf was healthy, i should replace the nonworking with liveCD one. So I booted in liveDVD and there was a problem - there was only one resolution 640x480 (why did that change???). 

my computer: radeon 9550 128mb; monitor LG 99G (max 1600x1200@75hz, 1280x1024@85Hz).
Please help me, so Ubuntu wouldn't go to group of about six other linux distros, who didn't last for a week on my computer...

---

### Post by shrift on 2006-06-04
You should read this first and take a few notes before you try this.

exit your desktop with this command: ```
sudo /etc/init.d/gdm stop
```
that will bring you to a terminal, login, then do this:```
sudo dpkg-reconfigure xserver-xorg
```
This will run you through your setup of X. When it gets to it, tell it to try and guess your monitor configuration, then select eh correct monitor modes. Finish that program then do this:```
sudo /etc/init.d/gdm start
```

If that works, great. Otherwise, I did a bit of research and it looks like your displays refresh rate ranges are as below:

Horizontal 30 - 96 kHz
Vertical 50 - 160 Hz

To add those to your xorg.conf type this in a terminal ```
sudo gedit /etc/X11/xorg.conf
```

and under the "Monitor" section, change the "HorizSync" to "30 - 96" and the "VertRefresh" to "50 - 160" So when your done it should look kind of like this:
```
Section "Monitor"
        Identifier      "DELL P780"
        Option          "DPMS"
        HorizSync       30-85
        VertRefresh     48-120
EndSection

```

Also make sure that you have the proper resolutions under the "Screen" section. Mine looks like this: 
```

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV6 [Vanta/Vanta LT]"
        Monitor         "DELL P780"
        DefaultDepth    24
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

```

After that, restart your xserver: ```
sudo /etc/init.d/gdm stop
``` then once you are logged in to the console again ```
sudo /etc/init.d/gdm start
```

---

### Post by amonsul on 2006-06-04
or try this....

open terminal
"sudo -s"
write your password

then type

"gedit /etc/X11/xorg.conf"

then go under the "Device" section and add this line...

Option "DDCMode"




Now it works

---

### Post by RoyalShrubber on 2006-06-04
Thx shrift... now it works great :D :D :D :D :D :D :D 

now i just have to set up my wireless card (will be pain in the ***, but i have found help on net :-D )

---

