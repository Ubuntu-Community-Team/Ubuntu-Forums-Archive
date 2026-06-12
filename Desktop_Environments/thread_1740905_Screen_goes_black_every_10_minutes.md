---
title: "Screen goes black every 10 minutes"
date: 2011-04-27
forum: Desktop Environments
---

### Post by bigred1 on 2011-04-27
When watching movies (Totem player, in Maverick), the entire screen goes black regularly, every 10 minutes. Clicking with the mouse brings up the display again.

Under System->Preferences->Screensaver, the setting is 'regard the computer as idle after 2 hours.' Under Power Management, the display is to be put to sleep after 1 hour. So, there seems to be no setting to turn off the screen after 10 minutes.

Any ideas?

---

### Post by SantaFe on 2011-04-27
Yep, there isn't any way using power managements to do it, as I was having the same problem in Xfce.  However I discovered the xset command. ;)

Some info:
> 

usage:  xset [-display host:dpy] option ...
    To turn bell off:
        -b                b off               b 0
    To set bell volume, pitch and duration:
         b [vol [pitch [dur]]]          b on
    To disable bug compatibility mode:
        -bc
    To enable bug compatibility mode:
        bc
    To turn keyclick off:
        -c                c off               c 0
    To set keyclick volume:
         c [0-100]        c on
    To control Energy Star (DPMS) features:
        -dpms      Energy Star features off
        +dpms      Energy Star features on
         dpms [standby [suspend [off]]]     
              force standby 
              force suspend 
              force off 
              force on 
              (also implicitly enables DPMS features) 
              a timeout value of zero disables the mode 
    To set the font path:
         fp= path[,path...]
    To restore the default font path:
         fp default
    To have the server reread font databases:
         fp rehash
    To remove elements from font path:
        -fp path[,path...]  fp- path[,path...]
    To prepend or append elements to font path:
        +fp path[,path...]  fp+ path[,path...]
    To set LED states off or on:
        -led [1-32]         led off
         led [1-32]         led on
        -led named 'name'   led off
         led named 'name'   led on
    To set mouse acceleration and threshold:
         m [acc_mult[/acc_div] [thr]]    m default
    To set pixel colors:
         p pixel_value color_name
    To turn auto-repeat off or on:
        -r [keycode]        r off
         r [keycode]        r on
         r rate [delay [rate]]
    For screen-saver control:
         s [timeout [cycle]]  s default    s on
         s blank              s noblank    s off
         s expose             s noexpose
         s activate           s reset
    For status information:  q


I fixed it by opening a terminal & running the following commands one at a time after it's finished booting:

> 
xset dpms 0 0 0
xset -dpms
xset s noblank
xset s noexpose


Seems to work for me, haven't had a blank screen since.  And yeah, I know I could write a script file & have it start at bootup, but the only time I reboot is when a update requires it, so it's just as easy to do it manually. ;)  But if someone wants to show how to do it, it'd be neat.

Hope this helps somewhat. :popcorn:

---

