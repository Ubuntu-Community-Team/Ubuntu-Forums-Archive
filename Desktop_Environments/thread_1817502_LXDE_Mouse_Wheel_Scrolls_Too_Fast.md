---
title: "LXDE: Mouse Wheel Scrolls Too Fast"
date: 2011-08-03
forum: Desktop Environments
---

### Post by tgftw on 2011-08-03
I have Lubuntu (w/ LXDE) installed on my Netbook. everything is going great, but the touchpad for the netbook has a portion to the right, which is used as a mousewheel.

I haven't found anywhere to disable this, and it moves WAY too many lines at a time, probably 5 times faster than I'd care for.

I couldn't find any UI option to adjust this in OpenBox Config -> Mouse Settings.

I'd assume, albiet my Linux knowledge is very limited (obviously), that there's probably a console command to allow me to adjust this, or a configuration file somewhere I could open with a text editor.

I know how to do this in KDE, and I read a forum post about it in Gnome... but for the life of me, I cannot find this setting in LXDE; It may not even be available, given the nature of the environment.

Is there any way to achieve this? Thanks forums!

TLDR; How do you adjust scroll-wheel speed in LXDE?

EDIT: Forgot to mention, version is **Lubuntu 11.04**, fresh install.

---

### Post by ajgreeny on 2011-08-03
Try installing gpointing-device-settings and use that to set scrolling speed, if it offers that.  I personally used the terminal utility **synclient** but I only wanted to turn off tap-to-click, which drives me crazy.  My command just for interest is ```
synclient MaxTapTime=0
```

To see all the options synclient offers use ```
synclient -l
```but for scroll speed it should be ```
synclient VertScrollDelta=100
```as a start then play around with the final figure;  The higher the number the slower the scroll speed.

I am not sure if the setting is persistent, or if you may need to use a simple script file set to run at boot time, as I do for the tap-to-click problem

---

### Post by tgftw on 2011-08-06
Wow!

Incredible response.

Didn't even take into account the fact that I only have one post. I love these forums already.

Thanks a bunch, that does exactly what I need, haven't installed yet but the screenshots look very promising.

---

