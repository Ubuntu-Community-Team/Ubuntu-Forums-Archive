---
title: "Change screen format"
date: 2021-08-27
forum: Gaming &amp; Leisure
---

### Post by demonenero84 on 2021-08-27
He there):P,
I am using Kubuntu 21.04 with KDE Plasma Version: 5.21.4, is there a way to change your desktop format? I play old games that require a 4/3 format, right now I am using my monitor settings, I was wondering if there is an app that can change my format form 16/9 to 4/3.
My GPU is "Mesa Intel® HD Graphics 630" and it does not have any options to change format, by the way I am using wine to run those old games
Thanks in advance

---

### Post by mIk3_08 on 2021-08-27
Just go to the System Settings Apps of your Ubuntu Operating System.  Then go to Displays Settings. Then you can now change the resolution you  want.
System Settings App is located at the All apps Installed in your System. Just locate it there. or you can just run the command 
```
xrandr --output LVDS1 --panning "resolution" --scale "scale in numeric form ex.1.406x1.406"
```
Just change the resolution you want to be and the scale of the resolution and if you want to go back to the original resolution:
```
xrandr --output LVDS1 --scale 
```
For more about the xrandr run this command;
```
xrandr --help
```

---

### Post by demonenero84 on 2021-08-27
Thanks a lot :)

---

### Post by mIk3_08 on 2021-08-29
> **demonenero84 said:**
> Thanks a lot 
If you have nothing to add maybe you can mark this thread as solve.
marking this thread as solve is very easy just click the solve thread below
inside my signature so you will be guided. 
Marking this thread as solve might also help others who seek solutions same 
thread like this. So Good Luck and Regards.

---

### Post by mastablasta on 2021-08-30
4:3 works just fine on 16:9. they just get stretched. if game is well done you can use in game setting to change it to 16:9 resolution.

sometimes opensource engines are available for older games that will provide correct resolution for 16:9 monitors. For example doomsday engine (for Doom, Heretic, Hexen games), openmw (for Morrowind), dhewm3 (for doom 3), eduke32 (for Duke Nukem 3D), OpenJDK (for Jedi Knight 2 and Jedi Knight Academy) ...

---

### Post by demonenero84 on 2021-08-30
Thanks, marked as solved :P

---

