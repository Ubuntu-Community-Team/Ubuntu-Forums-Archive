---
title: "Top panel icons disappeared in gnome classic"
date: 2012-06-29
forum: Desktop Environments
---

### Post by wsabat on 2012-06-29
Hi
 
I use Ubuntu 12.04 and Gnome classic (no effects) GUI. All icons in the top right panel disappeared (I mean: calendar, sound volume, networks, logout and so on). I used 'alt+right mouse click' to add some icons such as power off, but not all are available. Can you suggest me a way of restoring the default top panel look?  
 
This topic:[ http://ubuntuforums.org/showthread.php?t=1429008&highlight=top+panel+icons]("http://ubuntuforums.org/showthread.php?t=1429008&highlight=top+panel+icons")
 looks similar to my problem, but I don't know how to add the Notification Area -applet to my panel.
 

 Thank you

---

### Post by Frogs Hair on 2012-06-29
Hello and Welcome
Try running the following from the terminal one at a time. (Ctrl + Alt + T) ```
gconftool --recursive-unset /apps/panel
``````
rm -rf ~/.gconf/apps/panel
``` ```
killall gnome-panel
``` If the terminal won't open you can try the command prompt. Alt + F2

---

### Post by kansasnoob on 2012-06-30
I believe what you're missing is the Indicator Applet. By default Ubuntu uses 'indicator-applet-complete'. I mocked up a screenshot here:

[http://ubuntuforums.org/showpost.php?p=11900657&postcount=12](http://ubuntuforums.org/showpost.php?p=11900657&postcount=12)

But be sure to look at this entire post:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

Particularly step #2.

---

### Post by kansasnoob on 2012-06-30
> **Frogs Hair said:**
> Hello and Welcome
Try running the following from the terminal one at a time. (Ctrl + Alt + T) ```
gconftool --recursive-unset /apps/panel
``````
rm -rf ~/.gconf/apps/panel
``` ```
killall gnome-panel
``` If the terminal won't open you can try the command prompt. Alt + F2

Are you sure that works with gnome 3?

I'm not saying it won't but I know a lot of the panel settings have moved to dconf. Look at this screenshot where gconf is on the left and dconf is on the right:

[ATTACH]220437[/ATTACH]

I'm NOT saying you're wrong, I just don't know :confused:

---

### Post by wsabat on 2012-07-03
Thank you both for help :)

@Frogs Hair - your solution has brought no effect. 
@kansasnoob - your hint works! thank you!

---

### Post by kansasnoob on 2012-07-03
> **wsabat said:**
> Thank you both for help :)

@Frogs Hair - your solution has brought no effect. 
@kansasnoob - your hint works! thank you!

Great :)

Would you please mark this thread solved.

---

### Post by Frogs Hair on 2012-07-03
> **kansasnoob said:**
> Are you sure that works with gnome 3?

I'm not saying it won't but I know a lot of the panel settings have moved to dconf. Look at this screenshot where gconf is on the left and dconf is on the right:

[ATTACH]220437[/ATTACH]

I'm NOT saying you're wrong, I just don't know :confused:

It was advertised to work with Gnome 3 on the blog I got the command from . Scratch that command for Gnome 3 !!

---

### Post by kansasnoob on 2012-07-03
> **Frogs Hair said:**
> It was advertised to work with Gnome 3 on the blog I got the command from . Scratch that command for Gnome 3 !!

We're cool .............. I'm still learning the ins and outs of the change from gconf to dconf. I think gconf will at some point be phased out altogether. No idea when ;)

---

